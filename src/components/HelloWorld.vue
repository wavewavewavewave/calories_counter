<template>
  <div id="app">
    <h1>Calorie counter</h1>
    <div>
      <label>Enter food:</label>
      <input v-model="foodName" placeholder="The name of the food">
      <label>Enter the calories:</label>
      <input v-model.number="calories" placeholder="Calories">
      <button v-on:click="addFood">Add</button>
    </div>

    <h2>Food list</h2>
    <ul>
      <li v-for="food in foods" :key="food.id">
        {{ food.name }} - {{ food.calories }} калорий
      </li>
    </ul>

    <p>Total calories: {{ totalCalories }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      foodName: "",
      calories: 0,
      foods: [],
    }
  },
  methods: {
    addFood() {
      if (this.foodName && this.calories > 0) {
        this.foods.push({ name: this.foodName, calories: this.calories });
        this.foodName = "";
        this.calories = 0;
      }
    },
  },
  computed: {
    totalCalories() {
      return this.foods.reduce((total, food) => total + food.calories, 0);
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
  margin: 0;
  padding: 0;
}

#app {
  background-color: #fff;
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

h1 {
  text-align: center;
  color: #333;
}

label {
  display: block;
  margin: 10px 0;
}

input {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 3px;
}

button {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

h2 {
  margin-top: 20px;
  color: #333;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 5px 0;
  padding: 10px;
  background-color: #f9f9f9;
  border: 1px solid #ccc;
  border-radius: 3px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

p {
  text-align: right;
  font-weight: bold;
  margin-top: 20px;
}
</style>
