<template>
  <div>
    <vue-tabs class="card" @on-error="handleError"
              v-model="tabNameCurrent" :tabsValue="tabNameNew">
      <!--<template slot="tab" scope="props">
        <li :class="{active:props.tab.active}" >
          <a href="" @click.prevent="props.clickHandler(props.index)" style="border-radius:50%">
           {{props.tab.title}}
          </a>
        </li>
      </template>-->
      <v-tab v-for="(re, index) in reList"
             :key="re.name"
             :title="re.name"
             icon="ti-user">
        {{re.name}}
      </v-tab>
    </vue-tabs>
    <button @click="reList.push({name:'test'})">Add more!</button>
    <button @click="reList.splice(0,1)">Remove first</button>
  <label>Tab index or name <input type="text" v-model="tabNameNew"></label>
  </div>
</template>

<script>

  export default {
    name: 'app',
    data(){
      return {
        reList : [],
        tabNameCurrent: 'name1',
        tabNameNew: 'name1',
      }
    },
    methods: {
      handleError(error){
        this.error = error
      }
    },
    mounted () {
      this.reList = [{name:'name1'},{name:'name2'},{name:'name3'}]
    }
  }
</script>
<style lang="scss">
  /*.vue-tabs .active_tab{
    background-color: #4caf50 !important;
    box-shadow: 0 4px 20px 0px rgba(0, 0, 0, .14), 0 7px 10px -5px rgba(#4caf50, 0.4) !important;
  }*/
  $border-radius-extreme: 6px !default;
  $white-color: white;
  $gray-input-bg: #F3F2EE !default;
  $card-black-color: #252422 !default;

  body {
    margin-top: 20px;
    background-color: #ecf0f1;
  }

  .card-footer {
    padding: 0px 20px;
  }

  .card {
    border-radius: $border-radius-extreme;
    box-shadow: 0 2px 2px rgba(204, 197, 185, 0.5);
    background-color: $white-color;
    color: $card-black-color;
    padding: 10px 0;
    margin-bottom: 20px;
    position: relative;
    z-index: 1;
  }

  .list-complete-item {
    transition: all 1s;
    display: inline-block;
    margin-right: 10px;
  }

  .list-complete-enter, .list-complete-leave-to
    /* .list-complete-leave-active for <2.1.8 */
  {
    opacity: 0;
    transform: translateY(30px);
  }

  .list-complete-leave-active {
    position: absolute;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s
  }

  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */
  {
    opacity: 0
  }

</style>
