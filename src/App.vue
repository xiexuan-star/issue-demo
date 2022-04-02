<script setup>
import { ref,shallowRef } from 'vue'
const foo = shallowRef({fooProp:1})
const bar = ref(1);
let nonReactive = 1
function onClick(){
  // #foo is updated
  foo.value.fooProp++;
  bar.value++;
  // when nonReactive changes, #nonReactive still has the old value 1
  // but in SFC playground, it will be updated to 2
  nonReactive++;
}
</script>

<template>
  <div id='foo'>
    {{foo.fooProp}}
  </div>
  <div id='bar'>
    {{bar}}
  </div>
  <div id='nonReactive'>
    {{nonReactive}}
  </div>
  <button @click='onClick'>
    clickme!
  </button>
</template>
