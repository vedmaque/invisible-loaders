<template>
  <div class="invisible-loaders-example">
    <h1>Invisile Loaders</h1>
    <div class="list">
      <div class="loader-item" v-for="item in items" :key="item.id">
        <div class="loader-item__descr">state: {{ item.state }}</div>
        <div class="loader-item__icon" v-show="item.state === 'loading'">
          <IconLoad />
        </div>
        <div class="loader-item__trigger">
          <button @click="toggleLoading(item)">toggle</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import IconLoad from '@/components/IconLoad.vue';

export default {
  name: 'App',
  components: {
    IconLoad,
  },
  data: () => ({
    items: [
      { id: 1, state: 'idle' },
      { id: 2, state: 'idle' },
      { id: 3, state: 'idle' },
      { id: 4, state: 'idle' },
    ]
  }),
  methods: {
    toggleLoading(item) {
      item.state = item.state === 'idle' ? 'loading' : 'idle'
    },
  },
}
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
.preloader-arc {
  fill: #989cb4;
}
.icon {
  display: inline-flex;
}
.icon svg {
  width: 24px;
  height: 24px;
  fill: currentColor;
}
.loader-item {
  display: flex;
  align-items: center;
  padding: 8px 16px;
}
.loader-item + .loader-item {
  border-top: 1px solid gray;
}
.loader-item__icon {
  margin-left: 16px;
  display: flex;
}
.loader-item__icon .icon {
  animation: rotate 1s linear infinite;
}
.loader-item__trigger {
  margin-left: auto;
}
.loader-item__trigger button {
  margin: 0;
  padding: 0;
  background-color: white;
  border: 1px solid blue;
  border-radius: 4px;
  padding: 8px;
}
@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
