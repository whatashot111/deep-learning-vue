<template>
  <div class="container">
    <div>
      <div v-if="browser">You are using Browser</div>
      <div v-else-if="android">You are using Android</div>
    </div>
    <div>
      <button @click="openApp">Open Instagram</button>
    </div>
  </div>
</template>

<script>
import { isBrowser, isAndroid } from "mobile-device-detect";
export default {
  name: "app",
  data() {
    return {
      browser: isBrowser,
      android: isAndroid,
    };
  },
  methods: {
    openApp() {
      if (this.android) {
        const url =
          "intent://instagram.com/#Intent;scheme=https;package=com.instagram.android;end";

        window.location.replace(url);
      } else if (this.browser) {
        window.location.replace("https://instagram.com");
      }
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  background: cyan;
  padding: 8px;
  border-radius: 8px;
  margin-top: 10px;
  cursor: pointer;
}
</style>
