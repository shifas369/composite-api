<template>
 
    <section class="vh-100 bg-image"
  style="background-image: url('https://gamlaa.com/wp-content/uploads/2014/07/bg-prlx-big-sky.jpg');">
   <div class="container justify-content-center align-items-center h-100">

    <div class="row justify-content-center align-items-center h-100">
      <div class="col-md-6 ">
          
        <div class="formbg">
         
        <h1>Login Here....</h1>
        <form @submit.prevent="submitForm" novalidate >
          <div class="form-group">
            <label for="name">Name:</label>
            <input type="text" id="name" v-model="name" class="form-control" :class="{ 'is-invalid': errors.name }" required>
            <div v-if="errors.name" class="invalid-feedback">{{ errors.name }}</div>
          </div>

          <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="email" class="form-control" :class="{ 'is-invalid': errors.email }" required>
            <div v-if="errors.email" class="invalid-feedback">{{ errors.email }}</div>
          </div>

          <div class="form-group">
            <label for="password">Password:</label>
            <input type="password" id="password" v-model="password" class="form-control" :class="{ 'is-invalid': errors.password }" required>
            <div v-if="errors.password" class="invalid-feedback">{{ errors.password }}</div>
          </div>

          <div class="form-group">
            <label for="phone">Phone:</label>
            <input type="tel" id="phone" v-model="phone" class="form-control" :class="{ 'is-invalid': errors.phone }" required>
            <div v-if="errors.phone" class="invalid-feedback">{{ errors.phone }}</div>
          </div>

          <button type="submit" class="btn btn-primary mt-3">Submit</button>
        </form>
        </div>
      </div>
    </div>

  </div>
    </section>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const name = ref('');
    const email = ref('');
    const password = ref('');
    const phone = ref('');
    const errors = ref({});

    const submitForm = () => {
      errors.value = {};

      // Validate name field
      if (!name.value.trim()) {
        errors.value.name = 'Name is required';
      }

      // Validate email field
      if (!email.value.trim()) {
        errors.value.email = 'Email is required';
      } else if (!/^\S+@\S+\.\S+$/.test(email.value)) {
        errors.value.email = 'Email is invalid';
      }

      // Validate password field
      if (!password.value.trim()) {
        errors.value.password = 'Password is required';
      } else if (!/(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*\W)/.test(password.value)) {
        errors.value.password = 'Password must contain at least one uppercase letter, one lowercase letter, one number, and one symbol';
      }

      // Validate phone field
      if (!phone.value.trim()) {
        errors.value.phone = 'Phone is required';
      } else if (!/^\d{10}$/.test(phone.value)) {
        errors.value.phone = 'Phone is invalid';
      }

      // Submit form if there are no errors
      if (Object.keys(errors.value).length === 0) {
        alert('Form submitted successfully!');
      }
    };

    return {
      name,
      email,
      password,
      phone,
      errors,
      submitForm,
    };
  }
}
</script>

<style>
.gradient-custom-3 {

background: #84fab0;


background: -webkit-linear-gradient(to right, rgba(132, 250, 176, 0.5), rgba(143, 211, 244, 0.5));


background: linear-gradient(to right, rgba(132, 250, 176, 0.5), rgba(143, 211, 244, 0.5))
}
.gradient-custom-4 {

background: #84fab0;

background: -webkit-linear-gradient(to right, rgba(132, 250, 176, 1), rgba(143, 211, 244, 1));


background: linear-gradient(to right, rgba(132, 250, 176, 1), rgba(143, 211, 244, 1))
}
.formbg{
  background-image: url(https://media.istockphoto.com/vectors/hexagons-gray-bg-vector-id1373203602?k=20&m=1373203602&s=612x612&w=0&h=wmF3LkBipuj7ZuC5OKQrDQDnLMAsJS6Rtvd4oKlDGQ8=);
  width: 100%;
  height: 100%;
  padding: 30px;
border-radius: 20px 20px 20px 20px;
align-content: center;

}
.formbg h1{
  text-align: center;
  color: orange;
  font-family:'Times New Roman', Times, serif,
  
}


</style>
