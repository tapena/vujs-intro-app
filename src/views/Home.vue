<template>
  <div class="home">
    <h1>Vue.js Reviews</h1>

    <div>
      Review: <input v-model="newReview.text">
      Rating: <input v-model="newReview.rating">
      Your Name: <input v-model="newReview.reviewer">
      <button v-on:click="addReview()">Add Review</button>
    </div>

    <div v-for="review in reviews" v-if="isPositive(review)">
      <h2>{{ review.reviewer }} - {{ review.rating }} Stars</h2>
      <p>{{ review.text }}</p>
    </div>

  </div>
</template>

<style>
  body {
    background-color: lightblue;
  }
</style>

<script>
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js! something",
      reviews: [
        { 
          text: "Vue.js is the best thing since sliced bread!",
          rating: 5,
          reviewer: "Burton Wax"
        },
        { 
          text: "I love Vue.js, especially when I'm programming!",
          rating: 4,
          reviewer: "Emily Post"
        },
        { 
          text: "Vue.js sucks.",
          rating: 1,
          reviewer: "Oscar the Grouch"
        }
      ],
      newReview: {text: "", rating: "", reviewer: ""}
    };
  },
  created: function() {},
  methods: {
    addReview: function() {
      if (this.newReview.text && this.newReview.rating && this.newReview.reviewer) {
        this.reviews.push(this.newReview);
        this.newReview = {text: "", rating: "", reviewer: ""};
      }
    },
    isPositive: function(inputReview) {
      var stupidCheck = inputReview.text.indexOf('stupid') === -1;
      var sucksCheck = inputReview.text.indexOf('sucks') === -1;

      return stupidCheck && sucksCheck;
    }
  },
  computed: {}
};
</script>






