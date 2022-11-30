<template>
  <div class="home">
  </div>
  <div class="container text-center" >
  <div class="row" >
    <div class="col-md-4 col-sm-12 mb-4 position-relative" v-for="post in posts" :key="post.id">
      <div class="card h-100 mb-4 border border-info" style="width: 18rem;">
   <img :src="post.image" class="card-img-top p-3" alt="..." width="100" height="250">
  <div class="card-body">
    <h5 class="card-title">{{post.title}}</h5>
    <h5 class="card-title text-danger">$ {{post.price}}</h5>
    <p class="card-text h-50">{{post.description}}</p>
    <a href="#" class="btn btn-success position-absolute bottom-0 end-75 mb-3" @click="singlePost(post.id)" >more details</a>
    
  </div>
</div>
    </div>
    
  </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HomeView',
  data(){
    return{
posts:[],

    }
  },
  created(){
    axios.get("https://fakestoreapi.com/products").then((res)=>{
     this.posts= res.data
    })

  },
  methods:{
    singlePost(idd){
      axios.get("https://fakestoreapi.com/products/"+idd).then((res)=>{
        console.log( res.data)
    })
   
  }
}
}

</script>
<style>
  
</style>
