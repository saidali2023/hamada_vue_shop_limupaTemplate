<template>
  <div>

            <!-- Li's Breadcrumb Area End Here -->
            <!-- Begin Li's Content Wraper Area -->
            <!-- <div class="breadcrumb-area">
                <div class="container">
                    <div class="breadcrumb-content">
                        <ul>
                            <li><a href="index.html">Home</a></li>
                            <li class="active">Login Register</li>
                        </ul>
                    </div>
                </div>
            </div> -->

            <!-- Li's Breadcrumb Area End Here -->
            <!-- Begin Login Content Area -->
            <div class="page-section mb-60">
                <br>
                <div class="container">
                    <div class="row">
                      <div class="col-sm-12 col-md-12 col-lg-6 col-xs-12">
                          <form action="#" method="post">
                              <div class="login-form">
                                  <h4 class="login-title">Register</h4>
                                  <div class="row">
                                      <div class="col-md-6 col-12 mb-20">
                                          <label>First Name</label>
                                          <input class="mb-0" type="text" placeholder="Name" v-model="name">
                                      </div>
                                      <div class="col-md-6 mb-20">
                                          <label>Email Address*</label>
                                          <input class="mb-0" type="email"  v-model="email" placeholder="Email Address">
                                      </div>
                                      <div class="col-md-6 mb-20">
                                          <label>Password</label>
                                          <input class="mb-0" type="password" placeholder="Password" v-model="password">
                                      </div>
                                      <div class="col-md-6 mb-20">
                                          <label>Confirm Password</label>
                                          <input class="mb-0" type="password" placeholder="Confirm Password">
                                      </div>
                                      <div class="col-12">
                                          <button class="register-button mt-0" @click.prevent="submitRegister">Register</button>
                                      </div>
                                  </div>
                              </div>
                          </form>
                      </div>

                    </div>
                </div>
            </div>

</div>
</template>

<script>
import router from '../routes/routes'
import axios from 'axios'
export default {
  data(){
    return {
      name:'',
      email: '',
      password: '',
    }
  },
  methods:{
      submitRegister() {
        axios.post('https://elnamat.com/poems/eshop/api/buyers/register',
            {
              name:this.name,
              email:this.email,
              password:this.password,
            }
          )
            .then((res) => {
                console.log(res);
                localStorage.setItem('usertoken', res.data.token);
                this.name = '';
                this.email = '';
                this.password = '';
                // router.push({name: 'GlobalHome'});
                // window.location.pathname = "/login";
            })
            .catch((err) => {
                console.log(err)
            })
      },
    }
}
  </script>
