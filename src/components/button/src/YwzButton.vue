<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  // 禁用
  disabled?: boolean
  // 类型
  type?:
    | 'primary'
    | 'secondary'
    | 'accent'
    | 'info'
    | 'success'
    | 'warning'
    | 'error'
    | 'ghost'
    | 'link'
  outline?: boolean
  size?: 'lg' | 'md' | 'sm' | 'sx'
}
const props = defineProps<Props>()
const classComputed = computed(() => {
  const classList = []
  props.disabled && classList.push('btn-disabled')
  props.type && classList.push('btn-' + props.type)
  props.outline && classList.push('btn-outline')
  props.size && classList.push('btn-' + props.size)
  return classList
})
</script>
<template>
  <button class="btn" :class="classComputed">
    <!-- 默认插槽 -->
    <slot></slot>
  </button>
</template>
<style scoped></style>
