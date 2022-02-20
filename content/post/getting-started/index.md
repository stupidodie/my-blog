---
summary: A note while learning c++.
draft: false
authors:
  - GuanranTai
lastmod: 2020-12-13T00:00:00Z
title: " Switch语句case标签的理解"
subtitle: ""
date: 2021-08-13T22:00:00.000Z
featured: false
tags:
  - C++
  - C
categories:
  - 编程
projects: []
image:
  caption: ""
  focal_point: ""
  placement: 2
  preview_only: false
---
Switch语句中，每个case没有单独的作用域，而在编译器在编译期间则会把变量的声明所需要的空间分配好。

可以如下进行理解：

```cpp
#include <iostream>
using namespace std;
int main() {
    bool b = false;
    goto case_false;
case_true:
    int ival;
    goto switch_end;
case_false:
    ival = 3;
    cout << ival << endl;
switch_end:
    return 0;
}
```

## C语言中对于Switch中定义变量的要求

在C语言中，对于Switch的语句要求如下：`case constant-expression : statement`，其中`constant-expression`可以是任意的表达式，而`statement`可以是任意的语句。
所以对于C语言来说，Switch语句中的case标签中的变量定义的要求是：

```c
case true : 
    ;
    int i = 3;
    break;
```

## C++中对于Switch中定义变量的要求

在C++中，对于switch语句的case标签中定义的变量的要求是：

```cpp
case true : 
{
    int i = 3;
    break;
}
```