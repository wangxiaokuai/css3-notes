# Flexbox 相关属性（12）
所有浏览器都支持，<mark>IE11以上支持</mark>
Flexbox完全颠覆了基于盒模型、基于float的布局思想。
Flexbox是灵活的布局，对不同的页面宽度有极强的适应性。
具体来说，Flexbox不需要用float，不用margin来制定盒子之间的边距。



CSS3 Flexbox Concepts
* flex container: display属性设为flex或inline-flex的元素
* flex item：flex container的一级子元素
* flex line: 一个隐藏的概念，控制flex item的排布。默认从左到右排布（多列）。 Flex items are positioned inside a flex container along a flex line.




## Flex容器的属性（6）

### （display）

flex

inline-flex






### flex-flow(shorthand)

The flex-flow property is a shorthand property for the flex-direction and the flex-wrap properties.




Default value: row nowrap

Inherited: no






###  flex-direction

控制排布方向


The  flex-direction  property specifies the direction of the flexible items inside the flex container. The default value of flex-direction  is  row  (left-to-right, top-to-bottom).

The other values are as follows:

*  row-reverse  - If the writing-mode (direction) is left to right, the flex items will be laid out right to left

*  column  - If the writing system is horizontal, the flex items will be laid out vertically

* column-reverse  - Same as column, but reversed





#### 用direction属性也可以改变方向
不推荐。。。


It is also possible to change the direction of the flex line.

If we set the  direction  property to  rtl  (right-to-left), the text is drawn right to left, and also the flex line changes direction, which will change the page layout:




```

body  {
     direction:  rtl;
}


```





### flex-wrap
控制item是否自动换行！默认不换行，都挤在一行里。。

The  flex-wrap  property specifies whether the flex items should wrap or not, if there is not enough room for them on one flex line.

The possible values are as follows（3）:



* nowrap - Default value. The flexible items will not wrap

* wrap - The flexible items will wrap if necessary

* wrap-reverse - The flexible items will wrap, if necessary, in reverse order




     Default value: nowrap









### justify-content
把每一行item当做一个整体，进行水平align的调整。默认是水平靠左排布的。

The  justify-content  property horizontally aligns the flexible container's items when the items do not use all available space on the main-axis.

The possible values are as follows:



* flex-start - Default value. Items are positioned at the beginning of the container

* flex-end - Items are positioned at the end of the container

* center - Items are positioned at the center of the container

* space-between - Items are positioned with space between the lines

* space-around - Items are positioned with space before, between, and after the lines






### align-items
调整一行item在垂直方向上的布局。默认是垂直拉伸排布的。

The  align-items  property vertically aligns the flexible container's items when the items do not use all available space on the cross-axis.

The possible values are as follows（5）:



* stretch - Default value. Items are stretched to fit the container

* flex-start - Items are positioned at the top of the container

* flex-end - Items are positioned at the bottom of the container

* center - Items are positioned at the center of the container (vertically)

* baseline - Items are positioned at the baseline of the container






### align-content
对多行进行布局控制。默认是垂直拉伸排布的。

The  align-content  property modifies the behavior of the  flex-wrap  property. It is similar to  align-items , but instead of aligning flex items, it aligns flex lines.

The possible values are as follows:

* stretch - Default value. Lines stretch to take up the remaining space
* flex-start - Lines are packed toward the start of the flex container
* flex-end - Lines are packed toward the end of the flex container
* center - Lines are packed toward the center of the flex container
* space-between - Lines are evenly distributed in the flex container
* space-around - Lines are evenly distributed in the flex container, with half-size spaces on either end



## Flex Item相关的属性（6）
### order  
灵活项目的手动排序
The  order  property specifies the order of a flexible item relative to the rest of the flexible items inside the same container:


### (Margin)
Setting  margin: auto;  will absorb extra space. It can be used to push flex items into different positions.
让浏览器自动填充外边距
#### Perfect Centering
用margin来实现完美的水平、垂直居中。
In the following example we will solve an almost daily problem: perfect centering.
It is very easy with flexbox. Setting  margin: auto;  will make the item perfectly centered in both axis:
### align-self
控制垂直布局
The  align-self  property of flex items overrides the flex container's align-items property for that item. It has the same possible values as the  align-items  property.

### flex(shorthand)


The flex property specifies the length of the item, relative to the rest of the flexible items inside the same container.
The flex property is a shorthand for the  **flex-grow, flex-shrink, and the flex-basis** properties.


    Default value: 0 1 auto
    Inherited: no


Special Values:
Values:
Value |Description
---|:---
auto |Same as 1 1 auto.
none |Same as 0 0 auto.
默认值 | Same as 0 1 auto. 


Usage:
```
.flex-container {
    display: flex;
    width: 400px;
    height: 250px;
    background-color: lightgrey;
}


.flex-item {
    background-color: cornflowerblue;
    width: 75px;
    height: 75px;
    margin: auto;
}
```
重写了flex容器的align-items 让一行里的每个元素自己定义自己的垂直定位方式。


定义每个flex元素的相对宽度，默认是1



### flex-basis
设置灵活元素的初始宽度。默认是由元素内容撑开的，没有内容则为0.
注意：flex-basis只影响最小宽度，最大宽度还是内容决定的
The flex-basis property specifies the initial length of a flexible item.


Default value: auto
Inherited: no


Usage:
```
div:nth-of-type(2) {
    flex-basis: 80px;
}
```
Values:
Value |Description
---|:---
auto |Default value. The length is equal to the length of the flexible item. If the item has no length specified, the length will be according to its content
number |A length unit, or percentage, specifying the initial length of the flexible item(s)


### flex-grow
指明这个元素时可以长胖的。在需要的时候（宽度没填满），flex-grow元素可以长胖来把宽度填满。
The flex-grow property specifies how much the item will grow relative to the rest of the flexible items inside the same container.
当值大于0时，就是可增长的。数字代表可以长胖的倍数。


Default value: 0
Inherited: no

### flex-shrink
指明这个灵活元素是可以缩小的。在需要的时候（宽度不够），flex-shrink元素可以缩小给其他人腾出空间
The flex-shrink property specifies how the item will shrink relative to the rest of the flexible items inside the same container.
当值为1时，是不可缩小的；大于1时，是可以缩小的倍数。


Default value: 1
Inherited: no























