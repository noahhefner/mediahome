<script>

export default {
  props: {
    service: null,
    url: null,
    image: null,
    keybind: null,
    target: null,
    keybindHidden: null
  },
  computed: {
    imagePath() {
      return `/config/images/${this.image}`;
    },
    keybindUpper() {
      return this.keybind.toUpperCase();
    }
  }
}
</script>

<template>
  <div class="tile-wrapper-inner">
    <a :href="this.url" :target="this.target">
      <div class="tile">
        <div class="tile-img-wrapper">
          <img :src="this.imagePath" :alt="this.service">
        </div>
        <div v-if="!this.keybindHidden" class="keybind-container">
          <p>{{ keybindUpper }}</p>
        </div>
      </div>
    </a>
  </div>
</template>

<style scoped>

.tile img {
  object-fit: fill;
  width: 100%;
  height: 100%;
}

.tile-wrapper-inner {
  padding: 0;
  margin: 0;
  border: 0;
  height: fit-content;
  width: fit-content;
  height: 80%;
  width: 90%;
}

.tile-img-wrapper {
  overflow: hidden;
  border: 0;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  border: 2px solid var(--border-color);
}

.tile:hover .tile-img-wrapper {
  border: 2px solid var(--hover-color);
  transform: scale(1.03);
  transition: border, transform 0.2s ease;
}

.tile:not(:hover) .tile-img-wrapper {
  border: 2px solid var(--border-color);
  transform: scale(1);
  transition: border, transform 0.2s ease;
}

.tile:hover .keybind-container {
  opacity: 0;
  transition: opacity 0.2s ease;
}

.tile:not(:hover) .keybind-container {
  opacity: 100%;
  transition: opacity 0.2s ease;
}

.tile {
  position: relative;
  display: flex;
  height: 100%;
  width: 100%;
}

.keybind-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 2rem;
  height: 2rem;
  background-color: var(--keybind-color);
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 100%;
  border: 2px solid var(--border-color);
  transform: translate(-50%, -50%);
}

.keybind-container p {
  margin: auto;
  color: var(--text-color);
  font-family: Consolas, monospace;
}

</style>
