<script setup>
import { ref, reactive } from 'vue';

const emit = defineEmits(["createTodo"]);
const todoState = reactive({
  todo: "",
  invalid: null,
  errMsg: "",
});

const createTodo = () => {
  emit('createTodo', todoState.todo);
};
</script>

<template>
  <div class="input-wrap">
    <input type="text" v-model="todoState.todo" />
    <button @click="createTodo()">Create</button>
  </div>
</template>


<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;

    &:focus {
      outline: none;
    }
  }

  button {
    padding: 8px 16px;
    border: none;
  }
}
</style>
