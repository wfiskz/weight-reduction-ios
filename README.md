# weight-reduction-ios

# iOS .ipa 文件大小优化

****************************
减少图片数量：减少图片生成，只采用 @3x。

减少不必要的系统和架构的适配。

****************************
资源优化：

去除无用资源：
相同的资源但名字不同的；
未使用的图片；
一倍图资源；
代码里面一些无用的文件，例如RENAME等。

资源压缩：
图片无损/有损压缩；[官网]（https://imageoptim.com/howto.html）  
音频压缩；
使用ASSETS.XCASSETS来管理图片；

h5页面远程化；

动态下载资源；（字体、图片、配置数据等非必须资源）

****************************

编译选项优化（Build Settings编译选项）：

Optimization Level设置为Fastest,Smallest;(默认release是此选项)
（Optimization Level 应该是编译器的优化程度。比较早期的时候，硬件资源是比较缺乏的。为了提高性能，开发编译器的大师们，都会对编译器(从c到汇编的编译过程)加上一定的优化策略。优化后的代码效率比较高，但是可读性比较差，且编译时间更长。优化是指编译器一级的措施，与机器指令比较接近，所以很可能会导致硬件不兼容，进而产生了目前遇到的软件装不上的问题。 他是编译器的行为，与代码理论上不相关。）

把Enable bitcode 修改为YES;
(bit code是什么：说的是bitcode是被编译程序的一种中间形式的代码。包含bitcode配置的程序将会在App store上被编译和链接。bitcode允许苹果在后期重新优化程序的二进制文件，而不需要重新提交一个新的版本到App store上。另外的解释：当提交程序到App store上时，Xcode会将程序编译为一个中间表现形式(bitcode)。然后App store会再将这个botcode编译为可执行的64位或32位程序。总之就是和瘦身有关。)

Strip Debug Symbols During Copy设置为YES;
新创建版本会默认YES。旧版本未知。作用还需研究下。

Strip Linked Product设置成YES；
作用是去掉调试的信息。（目前还要确认会否影响到错误日志的收集）

Symbols hidden by default 选项设置为YES。
作用:release时去除不必要的调试符号。
参考：[symbolicate工具环境设置](http://blog.csdn.net/dnj630/article/details/7321101)

Make Strings Read-Only设为YES。
字面意思就是变为只读属性。详细作用需要调研。

附录：
[配置参数的理解](http://blog.csdn.net/iitvip/article/details/9118499)
****************************
