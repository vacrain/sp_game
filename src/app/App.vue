<script setup lang="ts">
  import { watch, watchEffect } from 'vue'

  import { useSound } from '@vueuse/sound'
  import { useMagicKeys, whenever } from '@vueuse/core'
  import { STATIC_URL_AUDIO } from '../entry/const'
  import { SHUANG_DICT } from './dict'

  console.log(SHUANG_DICT)

  // sound
  const { play } = useSound(`${STATIC_URL_AUDIO}input_right.mp3`)

  // keyboard current
  const { current } = useMagicKeys()

  // 小鹤双拼
  const { en } = useMagicKeys({
    aliasMap: {
      en: 'f'
    }
  })

  whenever(
    () => current.has('a') && !current.has('b'),
    () => console.log('A is pressed but not B')
  )
</script>

<template>
  <!-- <button @click="play()">Play a sound</button> -->
</template>
