<template>
 <div>
    <div class="content-header bg-light shadow-sm">
      <div class="container">
        <div class="row mb-2">
          <div class="col-sm-6">
            <h1 class="m-0">  <small>Convocatorias</small></h1>
          </div><!-- /.col -->
          <div class="col-sm-6"><!-- {{ info.nom_pagina }} -->
            <ol class="breadcrumb float-sm-right">
              <li class="breadcrumb-item"><router-link  :to="'/'">Inicio</router-link></li>
              <li class="breadcrumb-item">Convocatorias</li>
              <!-- <li class="breadcrumb-item active">Top Navigation</li> -->
            </ol>
          </div><!-- /.col -->
        </div><!-- /.row -->
      </div><!-- /.container-fluid -->
    </div>
   <div class="container mt-4" style="margin-top:9px; margin-bottom: 9px;">
   
    <div class="card mt-6">
      <div class="card-header bg-secondary text-white">
       Listado de convocatorias
      </div>
      <div class="card-body">
        <table class="table table-bordered table-hover table-sm">
          <thead>
            <tr>
               <th class="column-title">NOMBRE DEL PROCESO</th>
                            <th class="column-title">BASES</th>
                            <th class="column-title">RESULTADO E. CURRICULAR</th>
                            <th class="column-title">RESULTADO E. ENTREVISTA</th>
                            <th class="column-title">RESULTADO FINAL</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(lista,index) in listadoconvocatroias" :key="index">
              <td :style="lista.color_fondo ">{{ lista.nom_proceso }} <span :class="lista.span">{{ lista.texto }}</span></td>
              <td>
              <!-- inscripcion -->
               <template v-for="ins in lista.detalle.inscripcion" ><a :href="ins.url_archivo" class="btn btn-outline-primary btn-sm" style="margin-top:3px" target="_blank">{{ ins.nom_archivo }}</a><br></template>
              </td>
              <td>
              <!-- curricular -->
               <template v-for="curr in lista.detalle.curricular" ><a :href="curr.url_archivo" class="btn btn-primary btn-sm" style="margin-top:3px" target="_blank">{{ curr.nom_archivo }}</a><br></template>
              </td>
              <td>
              <!-- entrevista -->
               <template v-for="entre in lista.detalle.entrevista" ><a :href="entre.url_archivo" class="btn btn-info btn-sm" style="margin-top:3px" target="_blank">{{ entre.nom_archivo }}</a><br></template>
              </td>
              <td>
              <!-- final -->
               <template v-for="fin in lista.detalle.final" ><a :href="fin.url_archivo" class="btn btn-success btn-sm" style="margin-top:3px" target="_blank">{{ fin.nom_archivo }}</a><br></template>
              </td>      
            </tr>
          </tbody>
        </table>
      </div>
    </div>
   </div>
 </div>
</template>

<script>
// import axios from "axios"

 export default {
   name: '',
   data () {
     return {
       listadoconvocatroias:{}
     }
   },
   props: [],
   components: {

   },
   created () {
     this.convocatorias();
   },
   mounted () {},
   methods: {
     convocatorias()
     { var url='/api/convocatorias';
       axios.get(url)
            .then(response=>{
              this.listadoconvocatroias=response.data.convocatorias;
            });
     }
   }
 }
</script>

<style lang="css" scoped>

</style>
