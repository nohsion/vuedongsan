<template>
  <div id="app">
    <div class="black-bg" v-if="isOpenModal == true">
      <div class="white-bg">
        <h4>상세페이지임</h4>
        <p>상세페이지 내용임</p>
        <button @click="isOpenModal = false">닫기</button>
      </div>
    </div>

    <div class="menu">
      <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
    </div>

    <div v-for="item in oneRooms" :key= item.id>
      <img :src="item.image" class="room-img">
      <h4 @click="isOpenModal = true">{{item.title}}</h4>
      <p>{{item.content}}</p>
      <p>{{item.price}} 원</p>
    </div>

  </div>
</template>

<script>

import data from './data/post.js'

export default {
  name: "App",
  data() {
    return {
      oneRooms: data,
      isOpenModal: false,
      menus: ["Home", "Shop", "About"],
      prices: [70, 80, 90],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase(i) {
      console.log(i, this.reports[i])
      this.reports[i] += 1
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
