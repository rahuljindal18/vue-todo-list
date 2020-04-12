<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>

<script>
// import { v4 as uuidv4 } from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(evt) {
      evt.preventDefault();
      const newTodo = {
        // id: uuidv4(),
        title: this.title,
        completed: false
      };
      //Send up to parent
      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>

<template>
  <div>
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        placeholder="Add Todo..."
        name="title"
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>
