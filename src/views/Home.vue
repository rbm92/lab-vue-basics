<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <h1>This is the homepage</h1>
    <section id="it2">
      <h2>Iteration 2</h2>
      <!-- <p>{{ 2 + 2 }}</p> -->
      <button @click="generate">Generate text</button>
      <p>{{ text }}</p>
    </section>

    <section id="it3">
      <h2>Iteration 3</h2>
      <button @click="toggle" v-if="isHidden">Show</button>
      <button @click="toggle" v-else>Hide</button>
      <p v-if="!isHidden">There you go, keep it up!</p>
    </section>

    <section id="it4">
      <h2>Iteration 4</h2>
      <p><button @click="show">Show cards</button></p>
      <article id="content">
        <div class="card" v-for="card in cards" :key="card.id">
          <h3>{{ card.title }}</h3>
          <p>{{ card.content }}</p>
        </div>
      </article>
    </section>

    <section id="it5">
      <h2>Iteration 5</h2>
      <p><button @click="change">Apply colour</button></p>
      <p :class="{ orange }">I need some colour bro</p>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  data() {
    return {
      text: "",
      isHidden: true,
      cards: [],
      orange: false,
    };
  },
  methods: {
    generate() {
      this.text = "Congratulations, you know how to click a button!";
    },
    toggle() {
      this.isHidden = !this.isHidden;
    },
    async show() {
      const result = await fetch("http://localhost:3000/cards");
      const finalRes = await result.json();
      this.cards = finalRes;
    },
    change() {
      this.orange = true;
    },
  },
};
</script>
