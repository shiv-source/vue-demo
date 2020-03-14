<template>
  <div>
    <!-- <div class="scroller" v-for="(list,index) in listData" :key="index">
      <ul>
        <li>
          <span>{{list.title}}</span>
          <span>{{list.body}}</span>
        </li>
      </ul>
    </div>-->
    <div>
      <form @submit.prevent="SendData">
        <label>
          <b>Email</b>
        </label>
        <input type="email" placeholder="Email" v-model="userdata.email" />
        <br />
        <label>
          <b>Password</b>
        </label>
        <input type="password" placeholder="Password" v-model="userdata.password" />
        <br />
        <button type="submit" class="btn btn-dark">Send</button>
      </form>
    </div>
  </div>
</template>

<script>
//import axios from "axios";

export default {
  name: "HelloWorld",
  data() {
    return {
      listData: [],
      listHeaders: [],
      userdata: {
        email: null,
        password: null
      }
      // email :'',
      // password: ''
    };
  },
  methods: {
    SendData: function(e) {
       e.preventDefault();
      this.axios.post('http://localhost:3000/user/signup',{
        email : this.userdata.email,
        password : this.userdata.password
      })
      .then(function(response){
        
        console.log("data sent");
        console.log(response);
      })
      .catch(function(error){
        console.log(error)
      })
    }
  }
};
</script>

