<template>
<slick
  ref="slick"
  :options="slickOptions"
  @afterChange="handleAfterChange"
  @beforeChange="handleBeforeChange"
  @breakpoint="handleBreakpoint"
  @destroy="handleDestroy"
  @edge="handleEdge"
  @init="handleInit"
  @reInit="handleReInit"
  @setPosition="handleSetPosition"
  @swipe="handleSwipe"
  @lazyLoaded="handleLazyLoaded"
  @lazyLoadError="handleLazeLoadError">
  <picture>
    <source srcset="https://picsum.photos/1200/1200?random=1" media="(min-width: 1300px)">
    <source srcset="https://picsum.photos/1250/600?random=1" media="(min-width: 1024px)">
    <source srcset="https://picsum.photos/1024/450?random=1" media="(min-width: 768px)">
    <source srcset="https://picsum.photos/768/768?random=1" media="(max-width: 768px)">
    <img src="https://picsum.photos/id/1015/1300/1000" alt="MDN">
  </picture>
    <picture>
    <source srcset="https://picsum.photos/1200/1200?random=2" media="(min-width: 1300px)">
    <source srcset="https://picsum.photos/1250/600?random=2" media="(min-width: 1024px)">
    <source srcset="https://picsum.photos/1024/450?random=2" media="(min-width: 768px)">
    <source srcset="https://picsum.photos/768/768?random=2" media="(max-width: 768px)">
    <img src="https://picsum.photos/id/1015/1300/1000" alt="MDN">
  </picture>
    <picture>
    <source srcset="https://picsum.photos/1200/1200?random=3" media="(min-width: 1300px)">
    <source srcset="https://picsum.photos/1250/600?random=3" media="(min-width: 1024px)">
    <source srcset="https://picsum.photos/1024/450?random=3" media="(min-width: 768px)">
    <source srcset="https://picsum.photos/768/768?random=3" media="(max-width: 768px)">
    <img src="https://picsum.photos/id/1015/1300/1000" alt="MDN">
  </picture>
    <picture>
    <source srcset="https://picsum.photos/1200/1200?random=4" media="(min-width: 1300px)">
    <source srcset="https://picsum.photos/1250/600?random=4" media="(min-width: 1024px)">
    <source srcset="https://picsum.photos/1024/450?random=4" media="(min-width: 768px)">
    <source srcset="https://picsum.photos/768/768?random=4" media="(max-width: 768px)">
    <img src="https://picsum.photos/id/1015/1300/1000" alt="MDN">
  </picture>
</slick>
</template>

<script>
  import Slick from 'vue-slick';
  export default {
    name: 'ImageSlider',
    components: { Slick },
    props: {
      images: Array
    },
    data() {
      return {
        slickOptions: {
          slidesToShow: 2,
          arrows: false,
          dots:true,
          responsive: [
            {
              breakpoint: 1300,
              settings: {
                slidesToShow: 1,
              }
            },
            {
              breakpoint: 1024,
              settings: {
                slidesToShow: 1,
              }
            },
            {
              breakpoint: 768,
              settings: {
                slidesToShow: 1,
                autoplay: true,
              }
            }
          ]
        },
      };
    },
    methods: {
        next() {
            this.$refs.slick.next();
        },

        prev() {
            this.$refs.slick.prev();
        },

        reInit() {
            this.$nextTick(() => {
                this.$refs.slick.reSlick();
            });
        },
        handleAfterChange(event, slick, currentSlide) {
            console.log('handleAfterChange', event, slick, currentSlide);
        },
        handleBeforeChange(event, slick, currentSlide, nextSlide) {
            console.log('handleBeforeChange', event, slick, currentSlide, nextSlide);
        },
        handleBreakpoint(event, slick, breakpoint) {
            console.log('handleBreakpoint', event, slick, breakpoint);
        },
        handleDestroy(event, slick) {
            console.log('handleDestroy', event, slick);
        },
        handleEdge(event, slick, direction) {
            console.log('handleEdge', event, slick, direction);
        },
        handleInit(event, slick) {
            console.log('handleInit', event, slick);
        },
        handleReInit(event, slick) {
            console.log('handleReInit', event, slick);
        },
        handleSetPosition(event, slick) {
            console.log('handleSetPosition', event, slick);
        },
        handleSwipe(event, slick, direction) {
            console.log('handleSwipe', event, slick, direction);
        },
        handleLazyLoaded(event, slick, image, imageSource) {
            console.log('handleLazyLoaded', event, slick, image, imageSource);
        },
        handleLazeLoadError(event, slick, image, imageSource) {
            console.log('handleLazeLoadError', event, slick, image, imageSource);
        },
    },
  }
</script>

<style lang="scss">
@import '../../scss/_variables.scss';
@import '../../scss/_mixins.scss';
@import '../../scss/slick.scss';

.slick-slider::after {
  content:"";
  position: absolute;
  top:0;
  bottom:0;
  height:100%;
  width: 100%;
  pointer-events: none;
background: rgb(65,181,178);
background: linear-gradient(14deg, rgba(65,181,178,0.9) 0%, rgba(65,181,178,0) 100%);
}
</style>