<template>


  <ul>
    <template>
      <template v-for="(item, key) in items">
        <sh4-sidebar-link
          :key="key"
          :to="{ path: item.path }"
          :icon="[ 'la la-file-text', item.meta.iconClass ]"
        >
          <span slot="title">{{ $t(item.displayName) }}</span>
        </sh4-sidebar-link>
      </template>
    </template>
  </ul>


</template>


<script>
  import {employerRoutes} from './EmployerRoutes'
  import {candidateRoutes} from './CandidateRoutes'
  import Sh4SidebarLink from './components/Sh4SidebarLink'

  export default {
    name: 'admin-sidebar',
    components: {
      Sh4SidebarLink,
    },
    props: {
      minimized: {
        type: Boolean,
        required: true,
      },
    },
    data() {
      return {}
    },

    created() {
      let current =  this.$route.path;
      let segments = current.split("/");
      console.log(segments[2])

      },

    computed: {
      // a computed getter
      items: function () {
        let current =  this.$route.path;
        let segments = current.split("/");
        if (segments[2] == 'candidate')
          return candidateRoutes.routes
         else
          return employerRoutes.routes
      }
    }
  }

</script>


<style lang="scss">
  $top-nav-height: 106.0625rem;
  $top-nav-bg: #0000FF;


  .va-navbar {
    transition: background-color .3s ease; /* sidebar's bg color transitions as well -> consistency */
    position: relative;
    height: 300px;
    background: $top-nav-bg;

    border: red 1px solid;


  }


</style>
