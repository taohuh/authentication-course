<template>
  <div>
    <form @submit.prevent="login">
      <label for="email">
        Email:
      </label>
      <input v-model="email" type="text" name="email">

      <label for="password">
        Password:
      </label>
      <input v-model="password" type="password" name="password">

      <button type="submit" name="button">
        Login
      </button>

      <p>{{ error }}</p>

      <router-link to="/register">
        Don't have an account ? Register.
      </router-link>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    login () {
      this.$store.dispatch('login', {
        email: this.email,
        password: this.password
      })
        .then(() => {
          this.$router.push('dashboard')
        })
        .catch(err => {
          this.error = err.response.data.error
          console.log('err', err.response.data.error)
        })
    }
  }
}
</script>

<style>

</style>
