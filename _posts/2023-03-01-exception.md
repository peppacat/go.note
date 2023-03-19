---
title: 异常处理
author: peppacat
date: 2023-03-01
category: Jekyll
layout: post
---

# 介绍
 go中的异常处理 defer panic recover
 抛出一个panic异常,在defer中通过recover捕获处理

```go
package mainpackage main

import (
	"errors"
	"fmt"
)

func main() {

	// go中的异常处理 defer panic recover
	// 抛出一个panic异常,在defer中通过recover捕获处理

	test()
	fmt.Println("Hello world")

	err := test1(-1)
	if err != nil {
		panic(err)
	}

}

func test() {
	// 匿名函数捕获异常
	defer func() {
		error := recover()
		if error != nil {
			fmt.Println("error = ", error)

		}
	}()
	var n1 int = 10
	var n2 int = 0
	var n3 int = n1 / n2
	fmt.Println("res = ", n3)
}

// 自定义异常
func test1(num int) error {
	if num < 0 {
		return errors.New("数据异常")
	} else {
		return nil
	}

}


```