<template>
  <main class="page">

    <h1 class="page-heading">
      Curved sections and borders PoC
    </h1>

    <ZeroMarkdownParser
      :markdown="content[0].raw"
      class="markdown" />

    <section class="poc">

      <div class="grid-equalHeight">
        <div class="col-6" data-push-left="off-0">
          <div class="title">
            heading heading heading
          </div>
        </div>
        <div
          class="col-6"
          data-push-right="off-0">
          <div class="example-1">
            <PocResponsiveClipper
              :breakpoints-x="[130, 480]"
              :breakpoints-y="[30, 150, 400, 530]">
              <template #svg-path>
                <PocResponsiveClipperTestSvg1 />
              </template>
              <template #clipped-content>
                <div class="squidgie"></div>
              </template>
            </PocResponsiveClipper>
          </div>
        </div>
      </div>

      <div class="grid">
        <div class="col-12">
          <div class="example-2">
            <PocResponsiveClipper
              :breakpoints-x="[50, 550, 720, 1220]"
              :breakpoints-y="[70, 290]">
              <template #svg-path>
                <PocResponsiveClipperTestSvg2 />
              </template>
              <template #clipped-content>
                <div class="bubbles"></div>
              </template>
              <template #overlay-content>
                <div class="content">
                  <div class="text">
                    Lörem ipsum plaliga tähåskapet relig men proktig telererar reabel, pangar. Geopuras ultrar megabesk otånera vanylig utan nylöbel soplabel.
                  </div>
                </div>
              </template>
            </PocResponsiveClipper>
          </div>
        </div>
      </div>

    </section>

  </main>
</template>

<script setup>
// ======================================================================== Data
const { data: content } = await useAsyncData('content', () => {
  return queryContent({
    where: {
      _path: { $contains: '/zero-ui/responsive-clipper' }
    }
  }).find()
})
</script>

<style lang="scss" scoped>
// ///////////////////////////////////////////////////////////////////// General
.poc {
  padding: 5rem 0;
}

.title {
  padding: 8rem 1rem;
  font-size: toRem(60);
  font-weight: 500;
}

.example-2 {
  margin-top: 3rem;
}

.content {
  padding: 5rem 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.text {
  color: white;
  font-weight: 600;
  font-size: toRem(20);
  text-align: center;
}

.bubbles {
  width: 100%;
  height: 100%;
  background-image: url('/poc/responsive-clipper/bubbles-wide.jpg.webp');
  background-size: 1200px 801px;
  background-position: center;
}

.squidgie {
  width: 100%;
  height: 100%;
  background-image: url('/poc/responsive-clipper/bubbles-1.jpeg');
  background-size: 600px;
  background-position: center;
}
</style>
