<template>
    <div class="container">
        <app-new-quote @quoteAdded = "createQuote"></app-new-quote>
        <app-quote-grid :quotes = "quotes" @quoteDeleted = "deleteQuote"></app-quote-grid>
        <div class="row">
            <div class= "col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a quote to delete it.</div>
            </div>
        </div>
        
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue';
import NewQuote from './components/NewQuote.vue';
    export default {
        data(){
            return {
                quotes: ['somethign'],
                maxQuotes: 10
            }
        },
        components: {
            'appQuoteGrid': QuoteGrid,
            'appNewQuote': NewQuote
        },
        methods: {
            createQuote(quote){
                if(this.quotes.length < this.maxQuotes){
                if(quote){
                    this.quotes.push(quote);
                }else {
                    alert("please enter some text")
                }
                }else {
                    alert("exceeded max quotes, delete a few.")
                }
            },
            deleteQuote(index){
                this.quotes.splice(index,1);
            }
        }
    }
</script>

<style>
</style>
