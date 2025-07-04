<template>
  <div class="login-container">
    <div class="d-flex justify-center align-center" style="height: 100vh;">
      <v-card
        class="login-card"
        elevation="12"
        color="#1e1e1e"
      >
        <v-card-text>
          <h1 class="text-h4 text-center mb-6" style="color: white;">Login</h1>

          <v-text-field
            :rules="[rules.required, rules.min]"
            label="Email"
            prepend-icon="mdi-email"
            color="primary"
            class="mb-4"
            v-model="email"
            outlined
          ></v-text-field>

          <v-text-field
            :append-icon="show4 ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[rules.required, rules.min]"
            :type="show4 ? 'text' : 'password'"
            label="Password"
            prepend-icon="mdi-lock"
            color="primary"
            class="mb-4"
            v-model="password"
            outlined
            @click:append="show4 = !show4"
            
          ></v-text-field>

          <v-checkbox
            label="Remember me"
            color="primary"
            class="mb-4"
            v-model="rememberMe"
          ></v-checkbox>

          <v-btn
            color="primary"
            elevation="2"
            block
            class="mb-6"
            @click="signIn"
          >
            Sign In
          </v-btn>

          <div class="text-center mb-4">
            <p style="color: white;">or</p>
          </div>
          

          <div class="google-btn-wrapper">
            <v-btn
              color="red darken-1"
              class="ma-2"
              elevation="2"
              @click="signInWithGoogle"
              block
            >
              <v-icon left>mdi-google</v-icon>
              Sign in with Google
            </v-btn>
          </div>
        </v-card-text>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'auth',
  data() {
    return {
      email: '',
      password: '',
      rememberMe: false,
      show4: false,
      rules: {
          required: value => !!value || 'Required.',
      }
    }
  },
  // methods: {
  //   signIn() {
  //     console.log('Email:', this.email, 'Password:', this.password, 'Remember me:', this.rememberMe)
  //   },
  //   async signInWithGoogle() {
  //     try {
  //       const result = await signInWithPopup(auth, provider)
  //       const user = result.user
  //       console.log('✅ Google user:', user)
  //       this.$router.push('/dashboard')
  //     } catch (error) {
  //       console.error('❌ Google sign-in failed:', error.message)
  //     }
  //   }
  // }
}
</script>

<style scoped>
.login-container {
  background-color: #524f4f;

}

.login-card {
  width: 100%;
  max-width: 500px;
  padding: 32px 24px;
  position: relative;
  border-radius: 16px;
}

.google-btn-wrapper {
  display: flex;
  justify-content: center;
}
</style>
