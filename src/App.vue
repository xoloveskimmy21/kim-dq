<script setup>

import { ref } from 'vue'

const products = [
  { name: "DQ® Sandwich", description: "Bite into a DQ® sandwich and taste the sensation of cool DQ soft serve nestled between two chocolate flavored wafers.", img: "https://dairyqueen.com.ph/wp-content/uploads/2015/12/dqsandwich.png" },
  { name: "Box of DQ® Sandwich", description: "Bite into a DQ® sandwich and taste the sensation of cool DQ soft serve nestled between two chocolate flavored wafers.", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/07/Box-of-DQ-Sandwich.png" },
  { name: "Dilly™ Bar", description: "A DQ® classic! Soft serve with a delicious coating of chocolate.", img: "https://dairyqueen.com.ph/wp-content/uploads/2015/12/dilly-bar.png" },
  { name: "Box of Dilly™ Bar", description: "A DQ® classic! Soft serve with a delicious coating of chocolate.", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/08/Box-of-Dilly-Bar.png" },
  { name: "Double Choco Dilly™ Bar", description: "A DQ® classic! Soft serve with a delicious coating of chocolate.", img: "https://dairyqueen.com.ph/wp-content/uploads/2022/05/DQ-WEB-Double-Choco-Dilly-Bar-04-1536x1536.png" },
  { name: "Strawberry Sundae", description: "For over 70 years DQ™ has been known for its great sundaes. Topped off with delicious hot fudge topping.", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/07/Strawberry-Sundae-1024x1024.jpg" },
  { name: "Chocolate Sundae", description: "For over 70 years DQ™ has been known for its great sundaes. Topped off with delicious hot fudge topping.", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/07/Chocolate-Sundae-1024x1024.jpg" },
  { name: "Mango Sundae", description: "For over 70 years DQ™ has been known for its great sundaes. Topped off with delicious hot fudge topping.", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/07/Mango-Sundae-1024x1024.jpg" },
  { name: "5oz Chocolate Dipped Cone", description: "Our famous original cone, truly a classic! Try it dipped in a crunchy chocolate coating.", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/06/5oz-Chocolate-Dipped-Cone.jpg" },
  { name: "5oz Vanilla Cone", description: "Our world's famous soft serve cone. Truly a classic!", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/06/5oz-Vanilla-Cone.jpg" },
  { name: "3oz Chocolate Dipped Cone", description: "Our famous original cone, truly a classic! Try it dipped in a crunchy chocolate coating.", img: "https://dairyqueen.com.ph/wp-content/uploads/2020/06/3oz-Chocolate-Dipped-Cone-491x1024.jpg" },
  { name: "3oz Vanilla Cone", description: "Our world’s famous soft serve cone. Truly a classic! ", img: "https://dairyqueen.com.ph/wp-content/uploads/2015/12/conos.png" },
]

const selected = ref(0)

</script>

<template>
  <div class="wrapper">
    <header>
      <h3>Kim's Dessert</h3>
    </header>
    <main>
      <div class="container">
        <!-- display products -->
        <div class="product" v-for="product in products" :key="product.name" @click="selected = product">
          <div class="product-image">
            <img :src="product.img" alt="product image" />
          </div>
          <div class="product-info">
            <h4>{{ product.name }}</h4>
          </div>
        </div>
      </div>
    </main>
    <div v-if="selected" class="modal" @click="selected = false">
      <div class="modal-content">
        <h3>{{selected.name}}</h3>
        <img :src="selected.img" alt="logo">
        <p>{{selected.description}}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Comforter+Brush&display=swap');

body {
  min-height: 100vh;
  align-items: flex-start;
  justify-content: flex-start;
}

#app {
  height: 100%;
  width: 100%;
  padding: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.wrapper {
  min-height: 100vh;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}

// blue theme 
header {
  width: 100%;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #1e90ff;
  color: white;
  font-size: 2rem;
  font-weight: 600;
  font-family: 'Comforter Brush', cursive;
}

main {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  margin-top: 2rem;
  width: 100%;
  height: 100%;
  max-width: 700px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  grid-template-rows: repeat(auto-fill, minmax(100px, 1fr));
  grid-gap: 2rem;
  align-items: center;
  justify-content: center;

  img {
    width: auto;
    height: auto;
    max-height: 100px;
    object-fit: cover;
  }
}

.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.4);
  display: flex;
  align-items: center;
  justify-content: center;

  .modal-content {
    background-color: #fefefe;
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 100%;
    max-width: 300px;
    border-radius: .5rem;

    img {
      width: auto;
      max-height: 200px;
    }
  }
}
</style>
