<template>
  <div
    class="list"
    :class="{ 'infinite-scroll-hidden': hidden }"
    v-infinite-scroll="triggerLoadMore"
    infinite-scroll-disabled="disabled"
    infinite-scroll-immediate-check="immediateCheck"
    infinite-scroll-distance="distance"
  >
    <div
      class="list-item"
      v-for="(item, index) in list"
      :key="index"
    >{{ item.id }}
    </div>
  </div>
</template>

<script>
import InfiniteScroll from '@/components/infinite-scroll'

export default {
  directives: {
    InfiniteScroll
  },

  props: {
    list: Array,
    disabled: Boolean,
    distance: Number,
    immediateCheck: {
      type: Boolean,
      default: true
    },
    onLoadMore: {
      type: Function,
      default () {
        return function () {}
      }
    },
    hidden: Boolean
  },

  methods: {
    triggerLoadMore () {
      this.onLoadMore()
    }
  }
}
</script>

<style scoped lang="scss">
  .infinite-scroll-hidden {
    overflow: scroll;
    height: 200px;
    display: none;
  }
</style>
