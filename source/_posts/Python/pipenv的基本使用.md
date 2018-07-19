---
title: pipenv的基本使用
date: 2018-05-30 09:44:43
tags: [Python, pipenv]
categories: Python
description: 
photo: "pipenv的基本使用/1.jpg"

timeline:
  - num: 1
    word: 2014/06/12-Start
  - num: 2
    word: 2014/11/29-XXX
  - num: 3
    word: 2015/02/18-DDD
  - num: 4
    word: More11
layout: timeline
toc: true
---
![pipenv的基本使用/1.jpg](pipenv的基本使用/1.jpg)
pipenv 是 Pipfile 主要倡导者、requests 作者 Kenneth Reitz 写的一个命令行工具，主要包含了Pipfile、pip、click、requests和virtualenv。Pipfile和pipenv本来都是Kenneth Reitz的个人项目，后来贡献给了pypa组织。Pipfile是社区拟定的依赖管理文件，用于替代过于简陋的 requirements.txt 文件。
<!--more-->
Pipfile的基本理念是：
Pipfile 文件是 TOML 格式而不是 requirements.txt 这样的纯文本。
一个项目对应一个 Pipfile，支持开发环境与正式环境区分。默认提供 default 和 development 区分。
提供版本锁支持，存为 Pipfile.lock。
click是Flask作者 Armin Ronacher 写的命令行库，现在Flask已经集成了它。

## 安装

安装pipenv

``` cmd
pip install pipenv
```

然后将目录更改为包含你的Python项目的文件夹，并启动Pipenv

``` cmd
cd my_project
pipenv install
```

这将在项目目录中创建两个新文件Pipfile和Pipfile.lock，如果项目不存在，则为项目创建一个新的虚拟环境。 如果你添加–two或–three标志到上面的最后一个命令，它分别使用Python 2或3来初始化你的项目。 否则将使用默认版本的Python。

新的解释器位置如： ``C:\Users\AirBook\.virtualenvs\untitled1-Z1OETCoj\Scripts\python.exe``
如果使用Pycharm进行开发时候，可以使用这个路径进行配置解释器。

## 管理Python依赖关系

安装需要的Python包,比如：

``` cmd
pip install six
```

删除指定的Python包,比如：

``` cmd
pip uninstall six
```

可以通过更新Pipfile.lock来冻结软件包名称及其版本，以及其依赖关系的列表。 这可以使用lock关键字完成的。

``` cmd
pipenv lock
```

如果另一个用户克隆存储库，可以添加Pipfiles到你的Git存储库，这样他们只需要在他们的系统中安装Pipenv，然后键入``pipenv install``，Pipenv会自动找到Pipfiles，创建一个新的虚拟环境并安装必要的软件包。

## 管理开发环境

通常情况下，开发环境和测试环境的包环境是不一样的，比如开发环境中需要有单元测试包。Pipenv使用--dev标志将两个环境分开，如：``pipenv install --dev nose2``，使用``pipenv install``是不会安装nose2包的，使用``pipenv install -dev``会安装nose2的。

## 代码运行

在工程目录下运行：

``` cmd
pipenv run python my_project.py
```

如果你不想每次运行Python时都输入这么多，你可以在shell中设置一个别名，例如在Windows系统下:

``` cmd
doskey prp = pipenv run python
```

## 参考
1 https://www.jianshu.com/p/00af447f0005