---
title: 压缩文件美化探索：Kun
p: beautify_kun
date: 2021-12-12 16:11:03
tags: beautify
---

在平日里编码遇到一个问题，对于压缩文件js，有时候需要有个工具将其美化，beautify之类工具只能将其格式化。已经压缩的变量名无法还原。于是产生造一个轮子的想法。

我给它取名为Kun，即八卦中坤字。

## 目标
1. 格式化代码
2. 将超长的函数变为一个一个es模块
2. 对已经压缩的变量名还原为一起随机单词，使其变的可读。

## 实现方法
要实现以上目标，就要用到语法解析库。我选择了acorn做语法解析，代码修改完成后，使用escodegen来保存。具体实现顺序

1. 遍历语法树ast.
2. 编写block语句区块插件识别语句块
3. 编写largeFuncModlueTrans插件，完成对代码的模块化抽取
4. 编写randomName插件完成对压缩变量的重命名

## 目前进展
当前还处于遍历语法树阶段，代码已上传github,传送门: [Kun](https://gitee.com/shawumu/Kun)