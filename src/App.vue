<template>
  <div class="app">
    <input type="text" v-model="val" @keydown.enter="addTodo">
    <ul>
      <li v-for="todo in todos" :key="todo.id">{{ todo.title }}</li>
    </ul>
  </div>
</template>

<script setup>
// region Vue3简化写法
import { ref, reactive } from 'vue'

const todos = reactive([
  { id: '1', title: '起床', done: false },
  { id: '2', title: '吃饭', done: false },
  { id: '3', title: '睡觉', done: false }
])
let val = ref('')

function addTodo() {
  todos.push({
    id: todos.length,
    title: val.value,
    done: false
  })
  val.value = ''
}
// endregion
// region Vue3写法
// import { ref, reactive } from 'vue'
//
// export default {
//   setup() {
//     let val = ref('')
//     const todos = reactive([
//       { id: '1', title: '起床', done: false },
//       { id: '2', title: '吃饭', done: false },
//       { id: '3', title: '睡觉', done: false }
//     ])
//
//     function addTodo() {
//       todos.push({
//         id: todos.length,
//         title: val.value,
//         done: false
//       })
//       val.value = ''
//     }
//
//     return { val, todos, addTodo }
//   }
// }
// endregion
// region Vue2写法
// export default {
//     name: 'App',
//     data() {
//       return {
//         val: '',
//         todos: [
//           { id: '1', title: '起床', done: false },
//           { id: '2', title: '吃饭', done: false },
//           { id: '3', title: '睡觉', done: false }
//         ]
//       }
//     },
//     methods: {
//       addTodo() {
//         this.todos.push({
//           id: this.todos.length,
//           title: this.val,
//           done: false
//         })
//         this.val = ''
//       }
//     }
// }
// endregion
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
