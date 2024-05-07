<template>
  <div>
    <h1>{{ greeting }}</h1>
    <p :class="{ 'highlight': isHighlighted }" :style="{ color: textColor }">{{ inputText }}</p>
    <button @click="toggleHighlight">INPUT</button>
    <input type="text" v-model="inputText" placeholder="Masukkan nama barang" @input="updateIsHighlighted">
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const greeting = ref('Selamat datang!');
    const isHighlighted = ref(false);
    const inputText = ref('');
    const textColor = ref('black');

    const toggleHighlight = () => {
      isHighlighted.value = !isHighlighted.value;
    };

    const updateIsHighlighted = () => {
      if (inputText.value.toLowerCase() === 'vue') {
        isHighlighted.value = true;
        textColor.value = 'green';
      } else {
        isHighlighted.value = false;
        textColor.value = 'black';
      }
    };

    return {
      greeting,
      isHighlighted,
      inputText,
      toggleHighlight,
      updateIsHighlighted,
      textColor
    };
  }
};
</script>

<style scoped>
.highlight {
  
  background-color: rgb(39, 34, 87);
}

input[type="text"] {
  margin-top: 10px;
  padding: 5px;
  width: 200px;
  font-size: 16px;
}
</style>
