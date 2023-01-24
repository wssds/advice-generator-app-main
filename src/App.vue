<script setup>
import { ref, onMounted } from "vue";

const data = ref(null);
const fetchData = async () => {
  const response = await fetch("https://api.adviceslip.com/advice");
  data.value = await response.json();
  console.log(data.value);
};

onMounted(() => fetchData());
</script>

<template>
  <div v-if="data" class="content-box">
    <div class="content-box__advice-number-wrapper">
      <span class="content-box__advice-number">ADVICE # {{ data.slip.id }}</span>
    </div>

    <p class="content-box__text">
      {{ data.slip.advice }}
    </p>

    <div class="content-box__svg-line-wrapper__mobile">
      <svg width="295" height="16" xmlns="http://www.w3.org/2000/svg">
        <g fill="none" fill-rule="evenodd">
          <path fill="#4F5D74" d="M0 8h122v1H0zM173 8h122v1H173z" />
          <g transform="translate(138)" fill="#CEE3E9">
            <rect width="6" height="16" rx="3" />
            <rect x="14" width="6" height="16" rx="3" />
          </g>
        </g>
      </svg>
    </div>

    <div class="content-box__svg-line-wrapper__desktop">
      <svg width="444" height="16" xmlns="http://www.w3.org/2000/svg">
        <g fill="none" fill-rule="evenodd">
          <path fill="#4F5D74" d="M0 8h196v1H0zM248 8h196v1H248z" />
          <g transform="translate(212)" fill="#CEE3E9">
            <rect width="6" height="16" rx="3" />
            <rect x="14" width="6" height="16" rx="3" />
          </g>
        </g>
      </svg>
    </div>

    <button class="main-btn" @click="fetchData">
      <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M20 0H4a4.005 4.005 0 0 0-4 4v16a4.005 4.005 0 0 0 4 4h16a4.005 4.005 0 0 0 4-4V4a4.005 4.005 0 0 0-4-4ZM7.5 18a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Z"
          fill="#202733"
        />
      </svg>
    </button>
  </div>
</template>

<style scoped>
.content-box {
  display: flex;
  flex-direction: column;
  gap: 40px;
  color: var(--main-text-colour);
  background-color: #313a49;
  height: 300px;
  width: 330px;
  border-radius: 15px;
  position: relative;
}

.content-box__advice-number-wrapper {
  display: flex;
  justify-content: center;
}

.content-box__advice-number {
  color: var(--secondary-colour);
  margin-top: 15px;
}

.content-box__text {
  text-align: center;
  font-size: 20px;
  font-family: bold;
  width: 80%;
  line-height: 1.4;
  margin-inline: auto;
}

.content-box__svg-line-wrapper__mobile {
  position: absolute;
  bottom: 42px;
  left: 50%;
  transform: translateX(-50%);
}

.content-box__svg-line-wrapper__desktop {
  display: none;
}

.main-btn {
  position: absolute;
  border: none;
  border-radius: 100%;
  background: var(--secondary-colour);
  height: 60px;
  width: 60px;
  bottom: 0;
  right: 50%;
  transform: translateX(50%) translateY(50%);
  display: flex;
  justify-content: center;
  align-items: center;
  transition: ease-in-out 225ms;
}

.main-btn:hover {
  box-shadow: 0px 0px 35px 7px var(--secondary-colour);
  transition: ease-in-out 225ms;
}

@media (min-width: 1024px) {
  .content-box {
    width: 500px;
  }

  .content-box__text {
    font-size: 20px;
    width: 65%;
    line-height: 1.5;
  }

  .content-box__svg-line-wrapper__mobile {
    display: none;
  }

  .content-box__svg-line-wrapper__desktop {
    display: block;
    position: absolute;
    bottom: 42px;
    left: 50%;
    transform: translateX(-50%);
  }
}
</style>
