jQuery-tagEditor - Strict autocomplete tags
============================================

**This is a fork.**<br />
For the original source and tribute go to<br />
https://goodies.pixabay.com/jquery/tag-editor/demo.html<br />
or<br />
https://github.com/Pixabay/jQuery-tagEditor<br />

__Changes in comparision to the original:__

**autocomplete**
Tags need to be valid: Valid tags are those that are suggested by the autocomplete and NOTHING more.
This Version can prevent the user from choosing none-valid Tags / creating own ones.
This means **only** tags that are predefined and shown in the autocomplete menu can be chosen

```
diff jquery.tag-editor.autocomplete.js jquery.tag-editor.ORIGINAL.js
107,115c107
<             ed.click(function(e, closest_tag, source) {
<                if(o.check_autocomplete) {
<                   if(e.originalEvent === undefined) {  
<                      if(source !== 'autocomplete') 
<                         return;
<                      
<                   }
<                }
<                
---
>             ed.click(function(e, closest_tag){
123c115
<                 blur_result = true;
---
>                 blur_result = true
126c118
<                 blur_result = true;
---
>                 blur_result = true
191c183
<                             ed.trigger('click', [$('.active', ed).find('input').closest('li').next('li').find('.tag-editor-tag'), 'autocomplete']);
---
>                             ed.trigger('click', [$('.active', ed).find('input').closest('li').next('li').find('.tag-editor-tag')]);
267,273c259,264
<             if(!o.check_autocomplete)
<                ed.on('keypress', 'input', function(e){ 
<                    if (o.delimiter.indexOf(String.fromCharCode(e.which))>=0) {
<                        inp = $(this);
<                        setTimeout(function(){ split_cleanup(inp); }, 20);
<                    }
<                });
---
>             ed.on('keypress', 'input', function(e){
>                 if (o.delimiter.indexOf(String.fromCharCode(e.which))>=0) {
>                     inp = $(this);
>                     setTimeout(function(){ split_cleanup(inp); }, 20);
>                 }
>             });
371d361
<         check_autocomplete : true,

```
