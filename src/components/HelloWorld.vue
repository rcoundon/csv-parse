<script setup lang="ts">
import Papa from 'papaparse';


defineProps<{
  msg: string
}>()



async function fileChange(event) {

  const file = event.target.files[0];
  Papa.parse(file, {
    header: true,
    dynamicTyping: true,
    complete: (result) => {
      console.log(JSON.stringify(result.data, null, 2));
    }
  })
}


</script>

<template>
  <div class="greetings">
    <input type="file" id="myFile" name="filename" @change="fileChange">
    <input type="submit">
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
