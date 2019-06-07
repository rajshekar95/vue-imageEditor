<template>
    <div>
        <div class="imageEditorApp">
            <tui-image-editor ref="tuiImageEditor"
                              :include-ui="useDefaultUI"
                              :options="options"
                              @addText="onAddText"
                              @objectMoved="onObjectMoved">
            </tui-image-editor>
        </div>
    </div>
</template>
<script>

// To use the default UI, the svg files for the icons is required.
import './svgs/svg/icon-a.svg';
import './svgs/svg/icon-b.svg';
import './svgs/svg/icon-c.svg';
import './svgs/svg/icon-d.svg';
// Load Style Code
import './svgs/tui-image-editor.css';
import {ImageEditor} from './index';
export default {
     name : 'BuiltInEditor',
    components: {
        'tui-image-editor': ImageEditor
    },
    data() {
        return {
            useDefaultUI: true,
            options: {
                includeUI: {
                    initMenu: 'draw'
                },
                cssMaxWidth: 700,
                cssMaxHeight: 500
            }
            
        };
    },
    methods: {
        onAddText() {
        },
        onObjectMoved() {
        },
        prcoessSaveImage(event){
            var imageUrl = this.$children[0].editorInstance.toDataURL();
            console.log(imageUrl);
        }
    },
     mounted() {


        var html = '<button class="tui-image-save" style="background-color: #fdba3b;border: 1px solid #fdba3b;color: #fff;font-family: "Noto Sans", sans-serif;font-size: 12px">Save</button>'
    let find = document.querySelector('.tui-image-editor-header-buttons ');
   let div = document.createElement('div');
  div.innerHTML = html;
   find.appendChild(div);

    var el = document.querySelector('.tui-image-editor-header-buttons .tui-image-editor-download-btn');

    el.style.display = 'none';

    var el2 = document.querySelector('.tui-image-editor-header-logo');

    el2.style.display = 'none';


    document.querySelector('.tui-image-editor-header-buttons .tui-image-save').addEventListener('click', this.prcoessSaveImage)
  }
};
</script>
<style scoped>
.imageEditorApp {
    width: 1000px;
    height: 800px;
}

</style>