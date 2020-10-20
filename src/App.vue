<template>
  <div>
    <h3>TODO APP VUE 2</h3>
    <form @submit.prevent="processForm">
      <label>NEW TODO</label>
      <input type="text" v-model="newtodo" />
      <button type="submit">ADD TODO</button>
    </form>
    <button @click="deleteAll">DELETE ALL</button>
    <h3>LIST TODO</h3>
    <ul>
      <li v-for="(item, index) in todos" :key="index">
        <label :class="{ done: item.done }" @click="toggleDone(item)">{{
          item.newtodo
        }}</label>
        <button @click="remove(index)">X</button>
      </li>
    </ul>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  data() {
    return {
      newtodo: null,
      todos: [],
    };
  },
  methods: {
    processForm() {
      this.todos.push({
        done: false,
        newtodo: this.newtodo,
      });
      this.$set(this, "newtodo", null);
    },
    deleteAll() {
      this.$set(this, "todos", []);
    },
    toggleDone(todo) {
      todo.done = !todo.done;
    },
    remove(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
.done {
  color: red;
}
</style>
