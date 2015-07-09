# 第二章 温故 JavaScript

```js
var spa = (function($){
    // Module scope variables
    var config = {
        extended_height : 434,
        extended_title : 'Click to retract',
        retracted_height : 16,
        retracted_title : 'Click to extend',
        template_html : '<div class=""spa-slider></div>'
    },
    $chatSlider,
    toggleSlider,
    onClickSlider,
    initModule;

    //Pulic Method
    initModule = function($container){
        $container.html (configMap.template_html);
        $chatSlider = $container.find('.spa-slider');
        $chatSlider.attr('title',configMap.retracted_title)
            .click(onClickSlider);
        return true;
    };

    return { initModule : initModule};

    })(jQuery);
```

这里我们将所有的 JavaScript 声明和 大多数的赋值合在一起，放在声明它们的函数顶部，这样变量的作用域就比较直观。

```js
//best practice
function(){
    var i;
    for(i=0;i<10;i++){
        //……
    }
}
```

## 高级变量提升和执行环境对象

在执行 JavaScript 函数时，JavaScript 引擎会首先分析代码，主要做三件事：

1. 声明和初始化函数参数；
2. 声明局部函数，包括将匿名函数赋给一个局部变量，但并不初始化它们；
3. 声明并初始化函数。