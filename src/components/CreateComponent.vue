<template>
    <div class="row justify-content-center">
        <div class="col-md-6">
            <!-- Content goes here -->
            <h1>Register</h1>
            <form @submit.prevent="handleSubmitForm">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" class="form-control" v-model="username.name" required> 
                </div>
                <div class="form-group">
                    <label for="ID">ID</label>
                    <input type="text" class="form-control" v-model="username.id" required> 
                </div>
                <div class="form-group">
                     <label for="Tel">Tel</label>
                    <input type="number" class="form-control" v-model="username.tel" required> 
                </div>


                <div class="form-group">
                    <button class="btn btn-success btn-block">Create</button>
                </div>
            </form>
            <router-link to="/">Back</router-link>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
        return {
            username: {
                name: '',
                id: '',
                tel: ''
            }
        }
    },
    methods: {
        handleSubmitForm() {
            const apiURL = 'http://apilazado.app.ruk-com.cloud/apiUser/create-username';
            axios.post(apiURL, this.username).then(() => {

            alert("ลงทะเบียนเรียบร้อย")
            this.$router.push('/');
            }).catch(error => {
                console.log(error)
                alert("ลงทะเบียนล้มเหลว")
                 this.$router.push('/');
            })
        }
    }
}
</script>