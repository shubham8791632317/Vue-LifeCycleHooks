<template>
  <div>
    <h1>Introduction to Vue lifecycle hooks</h1>
    <h2><pre>
      There are eight lifecycle methods:

      01. Before create
      02. Created
      03. Before mount
      04. Mounted
      05. Before update
      06. Updated
      07. Before destroy
      08. Destroyed
    </pre></h2>
    <hr>
    <h1>{{name}}</h1>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data(){
    return{
      name: 'Shubham Singh'
    }
  },
// --------------------------------------------------------------------------------------------------------------
  // 01st Life cycle hook method : beforeCreate()
  // This is the very first lifecycle hook that gets called in Vue JS, 
  // it gets called immediately after the Vue instance has been initialized.

  beforeCreate(){
    alert('beforeCreate hook has been called');
    console.log('beforeCreate hook has been called');
    alert(this.name); //We cannot access data properties because it gets called immediately after the vue instance initialized.
  },
    //  This way at the beforeCreate stage, things like computed properties, watchers, events, 
    //  data properties , and manipulation are not set up yet.
  // --------------------------------------------------------------------------------------------------------------

    // 02nd Life cycle hook method : created()
    // At this stage, the Vue instance has been initialized and has activated the start of things 
    // like computed properties, watchers, events, data properties and manipulations that come with it.

    created(){
      alert('created hook has been called');
      console.log(`My Name is ${this.name} and type of name is ${typeof this.name}`);
    },
    
    // If you run the application you will quickly notice that the type of data can now be displayed. 
    // It was not possible at the beforeCreated stage because the activation that takes place here has 
    // not taken place at the time. However, the Vue instance has not been mounted at this stage so you 
    // cannot manipulate the DOM here, the element property is not available for use yet.
// --------------------------------------------------------------------------------------------------------------

      // 03rd Life cycle hook method : beforeMount()
      // This is the next lifecycle hook that gets called after the created hook is called. 
      // This is the moment immediately before the instance is mounted on the DOM, the template 
      // and the scoped styles are all compiled here but you still cannot manipulate the DOM yet, 
      // the element property is not still available.

      beforeMount(){
        alert('beforeMount is called');
      },

// --------------------------------------------------------------------------------------------------------------
      // 04th Life cycle hook method : mounted()
      // This is the next lifecycle hook to be called after the beforeMount is called. 
      // It is called right after the instance has been mounted. Here the app component, or 
      // any other component in the project becomes functional and can now be used. 
      // The data is fit into the template, the DOM element is replaced with data filled element and 
      // can now be manipulated here, the element property is now available for use.

      mounted(){
        alert('mounted hook has been called');
      },

      // This is the default place any project created with the Vue CLI is at because the mounting 
      // is already done in the main.js file as we saw in the beginning. This is why you may not get 
      // to use the other hooks because the instance is already mounted by default for you.
// --------------------------------------------------------------------------------------------------------------
      // 05th Life cycle hook method : beforeUpdate()
      // This is the lifecycle hook called after the mounted hook, anytime a change is made to the data 
      // that requires the DOM to be updated. This stage is great for any logic before data changes like 
      // removing an event listener.
      
      // created(){
      //   alert(this.name);
      // },
      // beforeUpdate(){
      //   alert('beforeUpdate hook has been called');
      // },

      // mounted(){
      //   this.$data.name = "Suruchi Singh";
      //   console.log(this.name);
      // },

      // This originally has a welcome note on the DOM but in the mounted stage 
      // (which is where the DOM can be manipulated), the data gets changed and so the 
      // alert for beforeUpdate appears just before it changes.

// --------------------------------------------------------------------------------------------------------------
      // 06th Life cycle hook method : updated()
      // This lifecycle hook is called just after a DOM update has occurred, so this means 
      // immediately after the beforeUpdate hook is called. DOM related operations can be performed 
      // here, although it is not advisable to change state inside this hook as Vue already provides 
      // platforms specifically for that.

      // beforeUpdate(){
      //    alert('beforeUpdate hook has been called');
      // },

      // updated(){
      //    alert('Updated hook has been called');
      // },

      // mounted(){
      //    this.$data.name= 'lalalalallalalalalaalal';
      // },

// --------------------------------------------------------------------------------------------------------------
      // 07th Life cycle hook method : beforeDestroy()
      // This Vue lifecycle hook is called just before a Vue instance is destroyed, 
      // the instance and all the functionalities are still intact and working here. 
      // This is the stage where you can do resource management, delete variables and clean up the component.

     beforeDestroy(){
         alert('beforeDestroy hook has been called');
         this.name = null;
         delete this.name;
         console.log(this.name);
     },

// --------------------------------------------------------------------------------------------------------------
      // 08th Life cycle hook method : destroyed()
      // This is the final stage of the Vue lifecycle where all the child Vue instances have been destroyed, 
      // things like event listeners and all directives have been unbound at this stage. 
      // It gets invoked after running destroy on the object.

      destroyed(){
        this.$destroy();  
        console.log(this);
      }

      // When you run the app and take a look at the console, you will see nothing.

// --------------------------------------------------------------------------------------------------------------
}
</script>

<style>

</style>