<template>
  <CollapseCardWrapper label="properties">
    <div class="level is-flex-direction-column">
      <div
        v-for="attr in attributes"
        :key="attr.key"
        class="level-item has-text-centered mb-4">
        <div>
          <p class="heading mb-1">{{ attr.key }}</p>
          <p class="title is-6">{{ attr.value }}</p>
        </div>
      </div>
    </div>
  </CollapseCardWrapper>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'nuxt-property-decorator'
import { emptyArray } from '~/utils/empty'
import { Attribute } from '../../types'

const components = {
  CollapseCardWrapper: () =>
    import('@/components/shared/collapse/CollapseCardWrapper.vue'),
}

@Component({ components })
export default class Properties extends Vue {
  @Prop({ type: Array, default: () => emptyArray<Attribute>() })
  public attributes!: Attribute[]
}
</script>
