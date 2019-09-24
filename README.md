# UnityLearn-Shader

### Shader 概述

1. Shader 是给GPU执行的程序，中文叫做着色器

2. Shader 是运行在图形处理单元上，可以让开发人员直接操作图形硬件渲染功能

3. Shader 能开发出很多好的效果，UV 动画（在模型上再贴一张图，不断改变贴图的纹理坐标，纹理不断滚动，如波光），水， 雾等一些特效，这些用程序开发出来比较困难，性能还不好

4. 渲染流水线（Shader 在标准流水线的基础上插入代码，进行干预，得到特殊效果），模型投影，定点着色

5. Shader一般主要有

   - 固定管线着色器（固定管线着色器）：慢慢会被淘汰
   - 顶点 shader（顶点片元着色器）：干预模型形态的 Shader，例如：将平面变成曲面
   - 像素 Shader（表面着色器）：干预像素着色的 Shader，例如：UV 动画

6. - 模型定点运算的时候，可以加入顶点 Shader 来干预顶点的位置

   - 顶点着色的时候，加入像素 Shader 来干预像素的上色



### GPU 编程语言

1. 什么是 Direct3D 和 OpenGL：显卡的 API
   - Direct3D：Windows
   - OpenGL：Linux，iOS，Android
2. 目前面向GPU的编程语言主要有三种：
   - HLSL 语言通过 Direct3D 编写的着色器程序，只能在 Direct3D 里面使用
   - Cg 语言 NVIDIA 和微软合作提供的语言,与 C 相似，Direct3D 和 OpenGL 都支持
   - GLSL语言 支持 OpenGL 上编写 Shader 程序
3. Unity 使用 ShaderLab 来进行着色程序的编写，对不同的平台进行编译，重点支持 Cg 语言



### Shader Lab 语法基础

定义一个 Shader，每一个着色程序都要有一个 Shader

```c
Shader “name” { // name shader名字
      // 定义的一些属性，定义在这里的会在属性查看器里面显示; 
      [Propeties]  
      // 子着色器列表，一个Shader必须至少有一个子着色器; 
       Subshaders: {....}
       // 如果子着色器显卡不支持，就会降级，即Fallback操作;
       [Fallback]
}
```

