<template>
  <div class="container">
    <h1>Mama</h1>
    <div class="image-container">
      <div class="card" v-for="(img, index) in images" :key="index">
        <img :src="img.src" :alt="`Image ${index + 1}`" />
        <button @click="downloadImage(img.src, img.name)">Download</button>
      </div>
    </div>
  </div>
</template>

<script>
import image1 from "./assets/image1.jpg";
import image2 from "./assets/image2.jpg";
// import image3 from './assets/image3.jpg'

export default {
  name: "App",
  data() {
    return {
      images: [
        { src: image1, name: "image1.jpg" },
        { src: image2, name: "image2.jpg" },
        // { src: image3, name: 'image3.jpg' }
      ],
    };
  },
  methods: {
    downloadImage(url, filename) {
      const link = document.createElement("a");
      link.href = url;
      link.download = filename;
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    },
  },
};
</script>

<style>
.container {
  padding: 20px;
  font-family: sans-serif;
}

.image-container {
  display: flex;
  gap: 20px;
}

.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

img {
  max-width: 200px;
  border-radius: 6px;
  border: 1px solid #ccc;
}

button {
  padding: 6px 12px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #2980b9;
}
</style>
