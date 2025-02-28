<script setup>
import { ref } from 'vue'
import countryList from './assets/data.json';

const countryCode = ref('');

const getCountryCode = (event) => {
  const { value } = event.target;
  countryCode.value = value;
  console.log(value);
}

const getPhoneNumber = (event) => {
  const { value } = event.target;
  console.log(`${countryCode.value.split('(')[0]}${value}`);
}

const resetField = (event) => {
  event.target.value = ''
}
</script>

<template>
  <div class="container">
    
  <!-- <input class="code" type="text" placeholder="Country code" :value="countryCode" disabled /> -->
  <div class="phone-number-container">
    <!-- <span class="prefix">{{ countryCode.split('(')[0] }}</span> -->
     <input class="country-code" list="selectCountryCode" 
        @change="getCountryCode" 
        value="+91 (India)"
        @focus="resetField" 
      />
    <datalist id="selectCountryCode">
      <option v-for="item in countryList" :value="`${item.dial_code} (${item.name})`" />
    </datalist>
    <input class="phone-number" type="text" placeholder="Phone number" @change="getPhoneNumber" />
  </div>
  <!-- <input class="phone" type="text" placeholder="Phone number" @change="getPhoneNumber" /> -->
  </div>
  
</template>

<style scoped lang="scss">
.container {
  display: flex;
}
.phone-number-container {
  display: flex;
  align-items: center;
  border: 1px solid #a0a0a0;
  border-radius: 5px;
  input {
    border: none;
    outline: none;
  }
  span {
    font-size: 13px;
  }
}
.country-code {
  background: #dedede;
  border-radius: 5px 0 0 5px;
  text-align: center;
}
input {
  border-radius: 5px;
  padding: 10px;
  margin-right: 5px;
  border: 1px solid #a0a0a0;
}
.code {
  margin-right: 10px;
  width: 90px;
}
.prefix {
  padding-left: 10px;
}
.phone-number {
  padding-left: 5px;
}
</style>
