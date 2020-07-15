
<template>
  <div id="app">


    <div>
  <nav class="navbar fixed-top navbar-expand-lg  navbar-light bg-light">
  <b-navbar toggleable="lg">
    <b-navbar-brand href="#"><img src="./assets/minthcm.png"></b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav class="ml-auto">
        <b-nav-item href="#">HOME</b-nav-item>
        <b-nav-item href="#">OPEN SOURCE</b-nav-item>
        <b-nav-item href="#">FEATURED</b-nav-item>
        <b-nav-item href="#">SUPPORT</b-nav-item>
        <b-nav-item href="#">NEWS</b-nav-item>
        <b-nav-item href="#">DOWNLOAD</b-nav-item>
        
        <button class="btn btn-light" type="submit" style="backgroud-color:#75dad">Demo</button>
         <b-nav-item href="#">CONTACT</b-nav-item>
            <b-nav-item href="#">LOGIN</b-nav-item>
      </b-navbar-nav>
</b-collapse>
  </b-navbar>
  </nav>
</div>


<div>
  <b-navbar class="nav">
    <b-navbar-nav>
      <h1>
          <span class="span">DOWNLOAD</span></h1>
    </b-navbar-nav>
  </b-navbar>
   <b-container class="bv-example-row" id="cont">
 
</b-container>
</div>


<form method="get">
<b-row id="row">
      <b-col>
        <b-container class="bv-example-row">
          <b-row>
            <span id="span1">RELEASE 3.0.5</span>
          </b-row>
          <b-row>
            <span id="span2">29.04.2020</span>
          </b-row>
          <b-row></b-row>
          <b-row>
            <b-col></b-col>
            <b-col id="col">
              <b-button variant="outline-light" class="btn" id="app1">DOWNLOADS🔗</b-button>
            </b-col>
            <b-col id="col">
              
              <b-button @click="onClick()" variant="outline-light" class="btn">RELEASE NOTES📝</b-button>
            
            </b-col>
           
          </b-row>
        </b-container>
      </b-col>
      <b-col>
        <img src="./assets/man.svg" alt />
      </b-col>
    </b-row>
    <b-container class="bv-example-row" id="container"></b-container>
    <b-container class="bv-example-row" id="container"></b-container>
    <b-container class="bv-example-row" id="container"></b-container>

    <div>
      <b-card-group deck>
        <b-card
          id="b1"
          style="max-width: 20rem;"
          img-src="./assets/list.svg"
          img-alt="number"
          img-top
        >
          <b-button variant="outline-light" class="btn">ORDER RELEASES</b-button>
          
          <br />
          <br />
          <b-card-text>Read about and download previous releases.</b-card-text>
        </b-card>

        <b-card
          id="b1"
          style="max-width: 20rem;"
          img-src="./assets/cloud.svg"
          img-alt="cloud"
          img-top
        >
          <b-button variant="outline-light" class="btn">CLOUD SOLUTION</b-button>
          <br />
          <br />
          <b-card-text>Looking for a HCM system in a cloud?</b-card-text>
        </b-card>
        <b-card
          id="b1"
          style="max-width: 20rem;"
          img-src="./assets/book.svg"
          img-alt="book"
          img-top
        >
          <template v-slot:header></template>
          <b-button variant="outline-light" class="btn">DOCUMENTATION</b-button>
          <br />
          <b-card-text>We prepared a whole Wiki for you.</b-card-text>
          <template v-slot:footer></template>
        </b-card>
      </b-card-group>
    </div>



    <br />
    <br />
    <br />
    <br />
    <br />


 </form>

 <div>
      
<h3 style="margin-top:50px;">STAY UP TO DATE:</h3>
    <b-form>
    <b-form-group
      >  
        <b-form-input
          id="input"
          type="email"
          required
          placeholder="Enter email"
        ></b-form-input>
      </b-form-group>
       <b-form-group id="input-group-4">
        <b-form-checkbox-group  id="checkboxes">
          <b-form-checkbox value="me">Check me out</b-form-checkbox>
          
        </b-form-checkbox-group>
      </b-form-group>

      <b-button type="submit" variant="light"  class="btn">Submit</b-button>
      
    </b-form>
  </div>



</div>
</template>
<script>
import Vue from 'vue'
import axios from 'axios'
import Vueaxios from 'vue-axios'

Vue.use(Vueaxios,axios)

export default {
data () {
    return {
      info: null
    }
  },
  methods:{
async onClick () {
    

      axios.get('http://localhost:8087/downloadFile',
      {
        method: 'GET',
        responseType: 'blob',
         headers: {
            'Content-Type': 'application/json'
          }
      }).then(response => {
          var fileURL = window.URL.createObjectURL(new Blob([response.data]));
     var fileLink = document.createElement('a');
  
     fileLink.href = fileURL;
     fileLink.setAttribute('download', 'RELEASE-NOTES.txt');
     document.body.appendChild(fileLink);
   
     fileLink.click();
          })
        .catch(function (err) {
          console.log('FAILURE!!'+err)
        })
        }
  }
  
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#btn {
  background-color: white;
  color: black;
  font-size: 16px;
  cursor: pointer;
}
.btn {
  border-color: #75daad;
  color: black;
  font-weight: bold;
  margin-left: 50px;
}
.btn:hover {
  background-color: #75daad;
  color: white;
}
#container {
  height: 150px;
  display: grid;
  justify-content: space-evenly;
}
#b1 {
  padding: 3em;
  margin-inline-start: 8%;
  border: 0;
  height: 200px;
}
#row {
  height: 100px;
  margin-top: 10%;
  
}
#span1 {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 20px;
  line-height: 80%;
  font-weight: bold;
  margin-left: 14%;
}
#span2 {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 12px;
  line-height: 80%;
  font-weight: bold;
  margin-left: 14%;
  margin-top: 10px;
}
.nav{
  
   color: #75daad;
  margin-top:0px;
  
}
li{
  
  font-weight:450 ;
  height: 80px;
  width: 90px;
  margin-top:20px;
  margin-left: 40px;
}
li:hover{
  text-decoration: underline;
} 
#btn{
  
 
  background-color: white;
  color: black;
  font-size: 16px;
  cursor: pointer;
}
.btn{
  border-color: #75daad;
  color:black;
  font-weight: bold;
  margin-left: 50px;
  
 
}
.btn:hover {
  
  background-color: #75daad;
  color: white;
}
.nav{
    background: #16A085;
    height: 230px;
    margin-top: 160px;
}
.span{
    font-family: 'Noto Sans JP', sans-serif;
     color:white;
     margin-top: auto;
     font-size: 1.3em;
     line-height: 80%;
     font-weight: bold;
     }
#cont
{

height: 350px;
background-color: white;
margin-left: 0;
margin-right: 0;

}
#input{
width: 40%;
margin-left: 30%;
margin-right: 30%;
}
</style>
