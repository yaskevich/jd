<template>
  <n-message-provider>
    <n-layout position="absolute">
      <template v-if="store.state.token">
        <n-layout-header id="nav">
          <!-- <n-menu
          v-model:value="activeKey"
          mode="horizontal"
          :options="store.state.nav.options"
          @update:value="processMenu" /> -->
        </n-layout-header>
        <n-layout-content style="padding-bottom: 2rem">
          <n-space justify="center" class="nav">
            <router-link to="/">Map</router-link>
            <router-link to="/list">List</router-link>
          </n-space>
          <router-view />
        </n-layout-content>
        <n-layout-footer position="absolute" style="padding: 0.25rem">
          <n-space justify="center">
            <n-button text tag="a" href="https://yaskevich.com/" target="_blank">
              <template #icon>
                <!-- <n-icon :component="CameraAltFilled" /> -->
              </template>
              2023 •&nbsp;
              <!-- <strong>JD</strong> -->
              Alyaxey Yaskevich
            </n-button>
          </n-space>
        </n-layout-footer>
      </template>
      <template v-else>
        <Login />
      </template>
    </n-layout>
  </n-message-provider>
</template>
<script setup lang="ts">
import router from './router';
import { useRoute } from 'vue-router';
import { ref, onMounted, computed } from 'vue';
import { MenuOption, NIcon } from 'naive-ui';
import Home from './components/Home.vue';
import Login from './components/Login.vue';
import store from './store';
</script>

<style lang="scss" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.nav {
  padding: 1.5rem;
  div > a {
    text-decoration: none;
    color: #2c3e50;
    font-weight: 700;
    &.router-link-exact-active,
    &.router-link-active {
      color: #42b983;
    }
  }
}

.nav {
  margin-right: 5px;
}
</style>
