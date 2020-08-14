# C++学习实践笔记

前言：只是为了方便自己在学习和使用C++的过程当中将问题、收获记录的一个文档(同时上传github)

分类型分章节(慢慢添加，时长回顾)

## 一、未整理知识点(遗忘、有用的)

### 1.内存模型和名称空间

- 头文件

| 头文件类型  | 约定                | 示例       | 说明                                                  |
| ----------- | ------------------- | ---------- | ----------------------------------------------------- |
| C++旧式风格 | 以.h结尾            | iostream.h | C++程序可以用                                         |
| C旧式风格   | 以.h结尾            | math.h     | C、C++程序都可使用                                    |
| C++新式风格 | 无扩展名            | iostream   | C++程序可以用，使用namespace std                      |
| 转换后的C   | 加上前缀C，无扩展名 | cmath      | C++程序可以使用，可以使用不是C的特性，加namespace std |

- 名称空间

### 2.const和#define的比较

```cpp
#define MAX 100
const int Max = 100;
/*
1.使用第二种方式可以表明这个常量的类型
2.使用第二种方式可以使用C++的作用域规则将定义限定在特定的函数或文件中(这种方式不用在文件开头写，#是预编译的时候做的)
3.可以将const使用在更加复杂的类型(数组和结构)
*/
```

### 3.C++标准模板库(STL)	

### 4.字符串(String)

```c++
#include<stdio.h>
//C-style string,由于c中字符串是由\0结尾的
char dog[3]={'D','O','G'};			//not string!!
char cat[4]={'C','A','T','\0'};		//a string!!
//所以在C-style string中string其实就是使用数组存储的
//在c++中，如果使用第一种定义方式，再使用cout打印的话，由于cout是逐个字符打印的，所以会将dog数组打印完后，继续打印，直到碰到空
char DOG[]="dog";				   //此种方式可以隐式的不用加空
```

### 5.结构体(struct)

```cpp
//在c语言当中，当结构体定义完后，在创建自定义结构体变量时
struct type a;
//而在C++当中，省略struct
type a;
```

### 6.共用体

```cpp
//用处之一：当数据项使用两种或更多种格式(不会同时使用时),可以节省空间(常用于嵌入式开发的节省空间的需求)
//定义
union one4all
{
    int int_val;
    long long_val;
    double double_val;
};
//实现
one4all par;			     	//定义共用体变量
par.int_val=10;
cout<<par.int_val;				
par.double_val=1.38;			//现在存储的是double类型的数据变量，前面的int类型已经丢弃
//共用体每次只能存储一个数据，所以大小是按照占用最大空间的那个数据类型来取的
//配合使用
//定义：
struct widget
{
    char brand[20];
    int type;
	union id
	{
    	long id_num;
        char id_char[20];
	}id_val;
};
//实现
widget prize;				//定义一个自定义变量
if(prize.type==1)
    cin>>prize.id_val.id_num;
else
    cin>>prize.id_val.id_char;
//匿名共用体：没有名称，其成员将成为位于相同地址处的变量，但是每次也只能有一个是
struct widget
{
    char brand[20];
    int type;
    union
    {
        long id_num;
        char id_char[20];
    };
};
//实现
widget prize;				//定义一个自定义变量
if(prize.type==1)
    cin>>prize.id_num;
else
    cin>>prize.id_char;
//由于共用体是匿名的，所以此时的id_num和id_char被视为prize的两个成员，他们的地址相同，所以不需要中间标识符id_var
```

### 7.枚举题

```cpp

```





## 二、整理完毕的知识点(将上面知识点整理到C++框架中)