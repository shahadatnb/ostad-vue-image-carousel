<script setup>
    import { ref, reactive } from 'vue';

    const images = reactive([
        {
            thumb: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
            full: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
        },
        {
            thumb: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=300&q=60",
            full: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
        },
        {
            thumb: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
            full: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
        },
        {
            thumb: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
            full: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60"
        }
    ]);

    const currentIndex = ref(0);

    const prevImage = () => {
      currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
    };

    const nextImage = () => {
      currentIndex.value = (currentIndex.value + 1) % images.length;
    };

</script>

<template>

<div class="carousel">
    <div class="carousel-inner">
      <img v-for="(image, index) in images" :key="index" :src="image.full" v-show="index === currentIndex" />
    </div>
    <button class="carousel-control-prev" @click="prevImage">Previous</button>
    <button class="carousel-control-next" @click="nextImage">Next</button>
  </div>

</template>

<style scoped>

    .carousel-inner {
    display: flex;
    justify-content: center;
    }

    .carousel-inner img {
    max-width: 100%;
    height: auto;
    }

    .carousel-control-prev,
    .carousel-control-next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: #f1f1f1;
    border: none;
    color: #333;
    padding: 10px 20px;
    cursor: pointer;
    }

    .carousel-control-prev {
    left: 10px;
    }

    .carousel-control-next {
    right: 10px;
    }
</style>
