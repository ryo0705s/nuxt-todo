<template>
  <section class="container">
    <h1>Todoリスト</h1>
    <div class="addArea">
      <!-- pages/index.vue -->
      <input
        type="text"
        name="addName"
        v-model="content"
        placeholder="タスクを入力してください"
      />
      <button class="button button--green" @click="insert">追加</button>
      <!-- <input
        type="text"
        name="addName"
        id="addName"
        placeholder="タスクを入力してください"
      />
      <button id="addButton" class="button button--green">追加</button> -->
    </div>
    <div class="Filter">
      <button class="button button--gray is-active">全て</button>
      <button class="button button--gray">作業前</button>
      <button class="button button--gray">作業中</button>
      <button class="button button--gray">完了</button>
    </div>
    <table class="Lists">
      <thead>
        <tr>
          <th>タスク</th>
          <th>登録日時</th>
          <th>状態</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <!-- pages/index.vue -->
        <tr v-for="(item, index) in todos" :key="index">
          <td>{{ item.content }}</td>
          <td>{{ item.created }}</td>
          <td>
            <button class="button">{{ item.state }}</button>
          </td>
          <td><button class="button button--delete">削除</button></td>
        </tr>
        <!-- <tr>
          <td>テスト</td>
          <td>2020-04-30 17:00</td>
          <td><button class="button button--yet">作業前</button></td>
          <td><button class="button button--delete">削除</button></td>
        </tr> -->
      </tbody>
    </table>
  </section>
</template>
<script>
// pages/index.vue
import { mapState } from 'vuex'

export default {
  data() {
    return {
      content: '',
    }
  },
  computed: {
    ...mapState(['todos']),
  },
  // pages/index.vue
  methods: {
    insert: function () {
      if (this.content != '') {
        this.$store.commit('insert', { content: this.content })
        this.content = ''
      }
    },
  },
}
</script>
<style>
/* 省略 */
</style>
