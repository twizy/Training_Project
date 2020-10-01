<template>
    <div class="container">

        <app-header >

            <div class="row">
                <div class="col-sm-12 mt-4">
                    <h3>Add item on list</h3>
                    <div class="progress">
                        <div class="progress-bar" role="progressbar" aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
                            :style="{width: (emptyItems / totalItems) * 100 + '%'}">
                            {{ emptyItems }} / {{ totalItems}}
                        </div>
                    </div>
                </div>
            </div>

        </app-header>

        <app-item-grid>

            <div class="row">
                <form>
                    <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                        <label>Item</label>
                        <textarea class="form-control" rows="3" v-model="it"></textarea>
                    </div>
                    <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                        <button class="btn btn-primary" @click.prevent="insert">Add item</button>
                    </div>
                </form>
            </div>

            <app-items v-bind:key="i.id" v-for="i in txt">
                 <div id="bor" class="col-sm-6 col-md-4 col-lg-3">
                    <div class="card">
                    <div class="card-body">
                        <p class="card-text">{{ i }}</p>
                        <a href="#" class="btn btn-danger">Delete</a>
                    </div>
                    </div>
                </div>
            </app-items>


 
           

        </app-item-grid>

        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Item to delete it!</div>
            </div>
        </div>
        
    </div>
</template>

<script>
    import Header from './components/Header.vue';
    import ItemGrid from './components/ItemGrid.vue';
    import Items from './components/Items.vue';

    export default {
        data: function () {
            return {
                emptyItems:0,
                totalItems: 10,
                it:'',
                txt:[]

            }
        },
        methods:{
        insert(){
            if(this.txt.length <10)
            {
                this.txt.push(this.it);
                this.emptyItems = this.txt.length; 
            }else{
                alert("Delete some item to add new");
            }
            this.it = ''
        },
        del(index){
            this.txt.splice(index,1);
        }
    },
        components: {
            appHeader: Header,
            appItemGrid: ItemGrid,
            appItems:Items
        },
    }

 

</script>

<style>
</style>
