<template>
  <b-container class="hours-log-page">
    <b-row>
      <b-col sm="8" offset-sm="2">
        <b-row class="mt-5 mb-4">
          <b-col>
            <h1>Projects</h1>
          </b-col>
          <b-col>
            <b-btn @click="$router.push({name: 'ProjectEntry'})" variant="primary">
              + Add New Project
            </b-btn>
          </b-col>
        </b-row>

        <b-row>
          <b-col>
            <v-select
              :options="options"
            />
          </b-col>
        </b-row>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import { mapActions, mapState } from 'vuex';

export default {
  name: 'Projects',
  // data(){
  //   return{
  //     options:[
  //       {label: 'Canada', code: 'ca'} ,
  //       {label: 'Canada2', code: 'ca'} 
  //     ]
  //   }
  // },
  computed: {
    ...mapState(['projects']),
    options() {
      return this.projects.map((option) => {
        return {
          ...option,
          label: (option.description),
          code: (option.name)
        }
      })
    }
  },
  mounted() {
    this.readProjects()
  },
  methods: {
    ...mapActions(['readProjects'])
  }
}
</script>
