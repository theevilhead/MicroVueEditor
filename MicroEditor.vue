<template>
    <div id="playground">  
        
        <div class="editor-area">
            <textarea v-model="htmlEditorHandler" @input="handleInput"  spellcheck="false" autocomplete="false" placeholder="HTML"></textarea>
            <textarea v-model="cssEditorHandler" @input="handleInput" spellcheck="false" autocomplete="false" placeholder="CSS"></textarea>
            <textarea v-model="jsEditorHandler" @input="handleInput" spellcheck="false" autocomplete="false" placeholder="JS"></textarea>
        </div>
        <div class="render-area">
            <iframe id="renderFrame"></iframe>
        </div>

    </div>

</template>


<script>


    export default {
        components: {

        },
        data() {
            return {
                iFrame : null,
                htmlEditorHandler : '',
                cssEditorHandler : '',
                jsEditorHandler : ''
            }
        },
        mounted : function() {
            this.iFrame = document.getElementById('renderFrame')
        },
        methods : {
            handleInput : function(){
                
                this.iFrame.srcdoc = `${this.htmlEditorHandler}<style>${this.cssEditorHandler}</style><script>${this.jsEditorHandler}<\/script>`

            }
        }
    }
</script>

<style lang="scss">

    html,body{
        margin: 0;
        padding: 0;
    }

    *{
        box-sizing: border-box;
    }

    #playground {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;

        iframe,textarea{
            border: 1px solid #d9d9d9;
        }

    }

    .editor-area{
        width: 100%;
        flex-grow: 1;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;

        textarea{
            height: 50vh;
            width: calc(33.333333% - 0)
        }

    }

    .render-area{

        width: 100%;

        iframe {
            width: 100%;
            height: 50vh;
        }
        
    }

</style>
