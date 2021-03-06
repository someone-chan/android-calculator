# 软件内容简介

## UI设计

该计算器由Android + Kotlin 进行开发，在UI设计上主要参考一些设计网站上的图片。界面的布局方式采用的是线性布局。为了友好用户，添加按钮的点击效果，为了突出输入与输出，在输入时输入框文字较大，得到结果后输入框文字变小，输出框文字变大。当输入框文字过长时，文字向左滑动；当输出框文字过长时，字体自动缩小。

## 功能实现

该计算器支持包含小数的实现混合运算。在算法上，使用`StringBuffer`对读到的数字和小数点进行存储，直到读到运算符，然后将其中的内容转为浮点数存入栈中。同时采用另一个栈存储运算符。运算符的优先级定义如下(其中isp为栈内优先数，icp为栈外优先数)

|      |  =   |  （  | ×  ÷  % | +  - |  ）  |
| :--: | :--: | :--: | :-----: | :--: | :--: |
| isp  |  0   |  1   |    5    |  3   |  6   |
| icp  |  0   |  6   |    4    |  2   |  1   |

* 若 icp(ch) > isp(top)，令ch进栈
* 若 icp(ch) < isp(top)，top退栈运算
* 若 icp(ch) == isp(top)，top退栈但不操作
