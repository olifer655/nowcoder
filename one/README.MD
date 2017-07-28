题目是下面这样的：
> 在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

我的写法：（好悲伤，发现自己东西有个毛病，只是为了写出来而写，都不会仔细想。烂的方法写出来，激励自己吧！come on ,baby!）

```js

function Find(target, array)
{
  var arry = array || []
  var i = 0;
  for (i; i < arry.length ; i++ ){
    let res
    if(Array.isArray(arry[i])){

         arry[i].map((c, index, arr) => {
            if(c === target) {

              res = arr
            }                
         })
    }

    if(Array.isArray(res)) {

      return res
    }
  }
}

```
此方法依次遍历每一个数组，如果数组非常的大，那么是一个很好性能的方式。下面来看看好的写法：

```js
function Find(target, array)
{
    var row = array.length;
    var i = row-1;
    var j = 0;
    while( i>=0 && array[i][j]){
        if (array[i][j]<target){
           j++;
        }
        else if (array[i][j]>target) {
           i--;
        } else {
           return true;  
        }
    }
    return false
}

```
题目给明了 `每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序` 这是一个有序的矩阵，选择左下角是最佳的起点遍历，当 `目标数据` 大于 左下角时，只需要依次遍历最后一行就OK了，否则判断上一行的第一个和 `目标数据`。
