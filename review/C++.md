## C++
### 1.sizeof

```cpp
class A{

}
class B{
public:
      b(){
      }
      ~b(){
      }
}
A a;
B b;
/*
空类型的实例求sizeof本来是0，但声明实例时会占用一定的空间,
在VS中每个空类型的实例占用1字节
*/
cout<<sizeof(a)<<endl;  //1 
/*
调用构造和析构函数只需要知道函数的地址，与类型的实例无关
*/
cout<<sizeof(b)<<endl;  //1
```
```cpp
int GetSize(int data[]){
    return sizeof(data);
}

int data1[] = {1,2,3,4,5};
int size1 = sizeof(data1);//数组大小，5个整数*4字节=20

int* data2 = data1;
int size2 = sizeof(data2);//指针大小，4字节

int size3 = GetSize(data1);//数组作为形参传递自动退化为指针

printf("%d%d%d", size1, size2, size3);//20 4 4
```
### 2.构造函数传参
```cpp
class A{
    //构造函数形参是自己的一个实例，会无限递归调用导致栈溢出
    A(A other){
    }
    //解决方法：把传值参数改成常量引用
    A(const A& other){
    }
}
```


