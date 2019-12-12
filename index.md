---
title: KAIST CS206 Data Structure
modified: 2019-12-12
---

# KAIST CS206 Data Structure

Made by 20190480 Won-Joon Lee

Textbook

- Goodrich, M. T., Tamassia, R., & Goldwasser, M. H. (2014). Data structures and algorithms in Java. John Wiley & Sons.
- Sedgewick, R., & Wayne, K. (2011). Algorithms, 4th Edition, Addison-Wesley Professional. https://algs4.cs.princeton.edu/home/

---

- [Basic Definition](#basic-definition)
- [Java basic](#java-basic)
- [Type Conversion](#type-conversion)
- [Function (Static Method)](#function-static-method)
- [OOP &amp; Data Abstraction](#oop-amp-data-abstraction)
- [Arrays](#arrays)
- [Singly Linked Lists](#singly-linked-lists)
- [Algorithm Analysis](#algorithm-analysis)
- [Recursion](#recursion)
- [Stacks / Queues](#stacks--queues)
- [Lists and Iterators](#lists-and-iterators)
- [Tree](#tree)
- [Priority Queues](#priority-queues)
- [Maps &amp; Hash Tables](#maps-amp-hash-tables)
- [Search Trees](#search-trees)
- [Sorting](#sorting)

---

## Basic Definition

**Data Type** Set of value (and set of operations)

- 값(과 연산)의 집합

**Variable** Name that refers to a value

- 값을 가리키는 이름

**Literal** Programming language representation of a value

- 값의 프로그래밍 언어식 표현

**Declaration Statement** associates a variable with a type

- 선언문: 변수에 타입을 지정 ex) `int a;`

**Assignment Statement** associates a value with a variable

- 대입문: 변수에 값을 지정 ex) `a=5;`

**Trace** Table of variable values after each statement

- 변수의 값의 변화를 표현한 표

**[public, private, protected, static, final](#public-private-protected-static-final)**

**Data Structure** Arrangement of data that enables efficient processing by a program

- 효율적인 처리를 할 수 있게 해주는 자료의 구조적 배열

---

## Java basic

**for**: i가 0부터 1씩 커지면서 n보다 작은 동안 반복

```java
for(int i=0;i<n;i++) {
  ...
}
```

**while**: 조건을 만족하는 동안 반복

```java
while(~~) {
  ...
}
```

**do ... while**: 실행 후 조건 불만족 시 중지

```java
do {
  ...
} while (~~);
```

**Scanner** java.util.Scanner

| Method          | Description                                                                                                                                                                  |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| hasNext()       | Returns true iff there is another token in the input stream                                                                                                                  |
| next()          | Returns the next token **string** in the input strea; NoSuchElementException                                                                                                 |
| hasNext*Type*() | Returns true iff there is another token in the input stream and it can be interpreted as the corresponding base type, _Type_(Boolean, Byte, Double, Float, Int, Long, Short) |
| next*Type*()    | Returns the next token in the input stream andreturn as the base type, _Type_                                                                                                |
| hasNextLine()   | Returns true iff the input stream has another line of text                                                                                                                   |
| nextLine()      | Advances the input past the current line ending and returns the input that was skipped                                                                                       |

```java
Scanner input = new Scanner(System.in);
int a = input.nextInt();
```

**Math**

| _type_ method(_type_ parameter)      | Description                   |
| ------------------------------------ | ----------------------------- |
| _double_ abs(_double_ a)             | absolute value of a           |
| _double_ max(_double_ a, _double_ b) | maximum of a and b            |
| _double_ min(_double_ a, _double_ b) | minimum of a and b            |
| _double_ sin(_double_ theta)         | sine function                 |
| _double_ cos(_double_ theta)         | cosine function               |
| _double_ tan(_double_ theta)         | tangent function              |
| _double_ exp(_double_ a)             | exponential (e^a)             |
| _double_ log(_double_ a)             | natural log (ln a)            |
| _double_ pow(_double_ a, _double_ b) | raise a to the bth power(a^b) |
| _long_ round(_double_ a)             | round to the nearest integer  |
| _double_ random()                    | random number in [0.1)        |
| _double_ sqrt(_double_ a)            | square root of a              |

| _type_ variable | Description           |
| --------------- | --------------------- |
| _double_ E      | value of e (constant) |
| _double_ PI     | value of π (constant) |

---

## Type Conversion

**Types of variables involved in data-type operations always must match the definitions**

- 타입을 지정해주면 변수는 그 타입에 맞춰서 입력되어야 합니다

### Automatic Type Conversion

Convert number to string for "+"

Make numeric types match if no loss of precision

- ex) `11*0.25`: int(11) &rarr; double(11.00)

### Function Call

Follows return type

- ex) `Integer.parseInt(String s)`: String &rarr; int

### Explicit Cast

For values that belong to multiple types, we can cast the specific type

- ex) small integers: can be short, int, long
- ex) double can be truncated to int
  - `(int)2.71828`: double &rarr; int, value is 2

**Relative Question (Exercise 1 - Q.1)**

| Expression                  | Type   | Value | Description                                |
| --------------------------- | ------ | ----- | ------------------------------------------ |
| `(7/2)*2.0`                 | double | 6.0   | -                                          |
| `"700"-"5"`                 | -      | N/A   | Illegal operation on String                |
| `700+5+"A"`                 | String | 705A  | int `705` converted to String              |
| `3+(int)Math.random()`      | int    | 3     | double in [0,1) truncated to int           |
| `Integer.parseInt("1.5*2")` | -      | N/A   | Cannot parse integer from String `"1.5*2"` |

---

## Function (Static Method)

### Implementation in Java

```java
1   public static double harmonic(int n) {
2     double sum = 0.0;
3     for(int i=1; i<=n; i++){
4       sum += 1.0/i;
5     }
6     return sum;
7   }
```

| Name               | Location               |
| ------------------ | ---------------------- |
| method declaration | Line 1                 |
| return type        | `double` (Line 1)      |
| method name        | `harmonic` (Line 1)    |
| param type         | `int` (Line 1)         |
| param name         | `n` (Line 1)           |
| method body        | Line 2~6               |
| local variable     | `sum` (Line 2)         |
| return statement   | `return sum;` (Line 6) |

Why `static`?

- Non-static method cannot be referenced from a static context(`main`)

**Scope of the variable** The code that can refer to it by name

- 그 변수가 유효한 범위

### Overloading

Using same name for static methods whose signatures differ

Commonly used to define the same operation for values of different types

- If matching signature is ambiguous, it results in a compile-time error since Java can't resolve the ambiguity

**The method signature** the method's name and parameter types

**Relative Question (Exercise 1 - Q.3)**

`foo(1, 5)` for `foo(int x, double y)` and `foo(double x, int y)`

---

## OOP & Data Abstraction

**Object-Oriented Programming(OOP)** 객체지향프로그래밍

- 객체(object)를 사용한 프로그래밍
- Abstraction / Encapsulation / Modularity의 특징이 있음

### Abstraction

**Abstract Data Type(ADT)**(=**Interface**) Mathematical model of a data structure that specifies the type of data stored, the operations supported on them

- 자료 구조가 포함하고 있는 변수의 타입과 이 자료 구조에서 사용할 수 있는 연산을 표현해 놓은 것

**Class** It specifies how the operations are performed in the body of each method. Realize an interface by modeling a concrete data structure

- ADT(Interface)가 변수의 타입과 연산의 종류만 포함하고 있다면 class는 이를 직접적으로 구현하고 있는 부분에 해당함
- **Java class implement an interface**

```java
public class ~~~ implements ??? { ...   // ???: Interface
```

- Name have to be capitalized in Java

### Encapsulation

**Instance** class를 바탕으로 생성된 object

- Every object is an instance of a class

  &rarr; Client can use ADT without knowing implementation details

### Modularity

- Using libraries to reuse code

### Application Programming Interface(API)

A list of constructor and instance methods

- Specify the behavior of a data type

```java
String s = new String("Hello, World");
int l = s.length();
```

| Action                                     | Location                     |
| ------------------------------------------ | ---------------------------- |
| declaring a variable                       | `String s`                   |
| create an object by invoking a constructor | `new String("Hello, World")` |
| invoke an instance method                  | `s.length()`                 |

### Implementation of Class

Instance variables

- Represent the data associated with an object of a class
- Each instance of a class maintains its own set of instance variables

(Instance) methods

- Operations on instance variables
- Accessor Methods (access on instance variables) & Update Methods (change value of instance variables)
- vs. Static Methods
  - Static methods can be called without creating an instance of the class
  - ex) `Math.sqrt(2.0)`
  - Instance methods invocation is associated with an instance

Constructors

- **Create an instance** of a class by using the **new** operator witha method that has the same name as the class
- No return type declaration
- Return value is reference to new object(instance)

**this** a reference to the instance upon which the method was invoked

- 호출한 instance가 자동으로 **this**가 됨
- instance method 내에서 instance variable을 호출하는 경우 `this.a` 형식의 코드를 사용하는 것이 맞으나, 이러한 식으로 직접 호출하는 경우는 `a`가 `this.a`만이 가능하기 때문에 생략할 수 있음

```java
public class Complex {
  // Instance variables
  private final double re;
  private final double im;

  // Constructor
  public Complex(double re, double im) {
    this.re = re;
    this.im = im;
  }

  // Instance methods
  public Complex plus(Complex b) {
    double real = this.re + b.re;  // this.re can be written in re
    double imag = this.im + b.im;
    return new Complex(real, imag);
  }
  ...
}
```

### public, private, protected, static, final

#### public vs private vs protected

- public: all classes may access the defined aspect
- protected: only subclass or class in the same package can access the defined aspect
- private: only code within that class can acess the defined aspect

#### static

- it is associated withe the class as a whole, rather than with each individual instance of that class.
- class 내에서 static 변수를 지정할 경우 이는 이 class로 만든 각각의 instance에서 서로 다르게 존재하는 것이 아니라, 공통으로 하나만 존재하는 것이다.

#### final

- 이러한 변수는 한 번만 값을 할당할 수 있고 이후에는 절대 변하지 않음을 보장한다.

**Relative Question (Exercise 1 - Q.2)**

```java
public class Rectangle {
  private double x, y;
  private double width;
  private double height;

  public Rectangle(double x0, double y0, double w, double h) {
    double x = x0;
    double y = y0;
    double width = w;
    double height = h;
  }

  public double area() {
    return width * height;
  }
}
```

1. What is wrong with the code fragment?

- constructor에서 새로운 변수를 만들어 값을 대입하는데, 이 때의 변수는 constructor가 끝날 경우 scope를 벗어남, 즉 사용이 불가능해진다. constructor의 본래 목적인 instance variable의 할당 역시 이루어지지 않아, instance variable은 기본값을 가지고 있는 상태이다.

2. Correct the code using Java. Do not invent new variables and methods.

```java
public Rectangle(double x0, double y0, double w, double h) {
  this.x = x0;
  this.y = y0;
  this.width = w;
  this.height = h;
}
```

(`this` is removable)

---

## Arrays

**Array** Indexed sequence of values of the same type

- Can process many values of the same type with index
- Indices starts from 0
- Accessing the value a[i] with i is extremely efficient

### Copying an array

To copy an array, create a new array and copy all the individual elements.

- If don't, i.e. `double[] b = new double[a.length]; b=a;`, then `b` just refer same array with `a`
- Similarly, `int[] a = {1, 2, 3}; int[] b = {1, 2, 3};`, then `Arrays.equals(a, b);` returns `false`

### Java Implementation

#### java.util.Arrays

It contains few static methods related to array

- `Arrays.toString(a)`, `Arrays.equals(a, b)`, ...

Code fragments below are all equivalent since default value of double is 0.0

```java
double[] a;
a = new double[4];
for(int i=0; i<4; i++)
  a[i] = 0.0;


double[] b = new double[4];

double[] c = { 0.0, 0.0, 0.0, 0.0 };
```

**Relative Question (Exercise 2 - Q.1)**

### Two-dimensional arrays

Doubly-indexed sequence of values

```java
double[][] a = new double[m][n];
```

#### Java basic support

| Code            | Operation                       |
| --------------- | ------------------------------- |
| `double[][] a;` | Declare                         |
| `a[i][j]`       | Refer by index                  |
| `a.length`      | Number of rows                  |
| `a[i].length`   | Number of columns for `i`th row |
| `a[i]`          | Refer to `i`th row              |

Code fragments are all equivalent since default value of int is 0

```java
int[][] a = new int[3][3];

int[][] b =
{
  {0, 0, 0},
  {0, 0, 0},
  {0, 0, 0}
};
```

### Arrays of Objects

- Array elements can be of any type since it can store not only primitive elements such as character, but also reference variables
- Create the array and create each object in the array

**Relative Question (Exercise 2 - Q.4)**

Correct the following code

```java
import java.util.Scanner;
//The names of the class and the method are not shown in this fragment.

Scanner input = new Scanner(System.in);
int n = input.nextInt();
Cat[] cats = new Cat[n];
for(int i=0; i<n; i++) {
  cats[i].meow();
  cats[i].eat();
}
```

- Problem: each object in the array is not created
- Corrected code

```java
Cat[] cats = new Cat[n];
for(int i=0; i<n; i++) {
  cats[i] = new Cat();
}
for(int i=0; i<n; i++) {
  cats[i].meow();
  cats[i].eat();
}
```

---

## Singly Linked Lists

### Linked data structure

- Advnatage: Variable size (easily resizable)
  - size is not fixed
  - proportional to current number of elements
- Disadvantage: sequential access (cannot access by index)
  - random access is not allowed

### Singly Linked List

- sequence of nodes, node contains element(value) and next(reference to its successor)
- if next is null, this node is 'tail'

### Nested Class

- To define a class that is strongly related with another class. In other words, it is a way of logically grouping classes that are only used in one place.
- In this case, we will define `Node` class as nested class since it will only be used inside `SinglyLinkedList` class.

### Generics

- Placeholder for type name in definition which will be substituted into concrete data type in clients
- ex) `Node` will be defined as `Node<E>` and inside its definition, we will refer `E` as type. Then, for `Node<String> a = new Node<String>`, `E` will be replaced into `String` for `a`
- Java does not permit the creation of arrays of generics.
  - Create an Object array and explicitly cast it.

```java
private E[] data = new E[capacity]; //illegal
private E[] data = (E[])new Object[capacity]; //correct
```

### Implementation

| Signatures    | Operation                                          |
| ------------- | -------------------------------------------------- |
| addFirst(E e) | Add element at the head of singly linked list      |
| addLast(E e)  | Add element at the tail of singly linked list      |
| removeFirst() | Remove element from the head of singly linked list |

```java
public static class SinglyLinkedList<E> {
  private static class Node {
    private E element;
    private Node<E> next;

    public Node(E e, Node<E> n) {
      element = e;
      next = n;
    }

    public E getElement() { return element; }
    public Node<E> getNext() { return next; }
    public void setNext(Node<E> n) { next = n; }
  }

  private Node<E> head = null;
  private Node<E> tail = null;
  private int size = 0;

  public SinglyLinkedList() {}

  public int size() { return size; }
  public boolean isEmpty() { return size == 0; }
  public E first() {
    if (isEmpty()) return null;
    return head.getElement();
  }
  public E last() {
    if (isEmpty()) return null;
    return tail.getElement();
  }

  public void addFirst(E e) {
    head = new Node<E>(e, head);
    if (size == 0) tail = head;
    size++;
  }

  public void addLast(E e) {
    Node<E> newest = new Node<E>(e, null);
    if(isEmpty()) head = newest;
    else tail.setNext(newest);
    tail = newest;
    size++;
  }

  public E removeFirst() {
    if (isEmpty()) return null;
    E answer = head.getElement();
    head = head.getNext();
    size--;
    if(size == 0) tail = null;
    return answer;
  }
}
```

---

## Algorithm Analysis

### Asymptotic Analysis

- Focus on the growth rate of the running time as a function of the input size n

### Big-Oh Notation

- ![Definition](http://www.sciweavers.org/tex2img.php?eq=f%28n%29%3DO%28g%28n%29%29%20%5Cleftrightarrow%20%5Cexists%20c%3E0%2C%20n_%7B0%7D%5Cge%201%5Ctext%7B%20s.t.%20%7Df%28n%29%3C%3D%20c%5Ccdot%20g%28n%29%5Ctext%7B%2C%20for%20%7Dn%5Cge%20n_%7B0%7D&bc=White&fc=Black&im=png&fs=12&ff=txfonts&edit=0)
- Use only the fastest-growing term
- Characterize a function as closely as possible (2n != O(n^2))
- Do not include constant factors and lower-order terms (3n+5 != O(3n))

\* linearithmic: O(nlogn)

#### Primitive operations

| Time Complexity | Example                           |
| --------------- | --------------------------------- |
| O(1)            | Adding two numbers                |
|                 | Assigning a value to a variable   |
|                 | Comparing two numbers             |
|                 | Length of the array               |
|                 | Access to the element in an array |
|                 | Calling a method                  |
|                 | Returning from a method           |
| O(n)            | Linear Search                     |
| O(n^2)          | Nested Loop                       |

---

## Recursion

**Recursion** is

- **Recursion** is
  - ...
  - **Recursion** is a technique by which a method makes one or more calls to itself during execution.

### Time Complexity of Recursion

It is related to how much it repeats totally

---

## Stacks / Queues

**Collection** ADT whose values are a multiset of items, all of the same type

- No limit on the size

### Stack vs. Queue

**Common Operations**

- Add an item to the collection (Push/Enqueue)
- Test if the collection is empty
- Rteurn the size of the collection

**Different Operation**

- **Stack** Remove and return the item _most_ recently added (Pop)
  - **LIFO** Last In First Out
- **Queue** Remove and return the item _least_ recently added (Dequeue)
  - **FIFO** First In First Out

### Performance specifications

- All operations are constant-time
- Memory use is linear in the size of the actual collection, when it is nonempty
- No limits within the code on the collection size

### Stack API

| return type | method(_type_ parameter) | Description                                                  |
| ----------: | :----------------------- | ------------------------------------------------------------ |
|        void | push(_E_ item)           | Add item to stack                                            |
|           E | pop()                    | Remove and return the element most recently pushed           |
|           E | top()                    | Return the element most recently pushed, without removing it |
|     boolean | isEmpty()                | Return whether the stack is empty                            |
|         int | size()                   | Number of elements in the stack                              |

- Assume `null` is returned from `top()` and `pop()` when stack is empty

### Array-based Stack

- Use an array to hold the collection

**Problems**

- Array may become full &rarr; limit on the collection size
- Memory use of array is fixed &rarr; nonlinear

### Linked list stack

**Variable size** can solve the problems

```java
public class LinkedStack<E> implements Stack<E> {
  private SinglyLinkedList<E> list = new SinglyLinkedList<E>();

  public LinkedStack() { }

  public int size() { return list.size(); }
  public boolean isEmpty() { return list.isEmpty(); }
  public void push(E element) { list.addFirst(element); }
  public E top() { return list.first(); }
  public E pop() { return list.removeFirst(); }
}
```

### Nested Node Stack

**Why?** We don't have to import SinglyLinkedList but directly uses private nested class Node

```java
public class StackNode<E> implements Stack<E> {
  private Node<E> first;
  private int n;

  private static class Node<E> {
    private E item;
    private Node<E> next;
  }

  public StackNode() {
    first = null;
    n = 0;
  }

  public boolean isEmpty() { return first == null; }
  public int size() { return n; }
  public void push(E item) {
    Node<E> oldFirst = first;
    first = new Node<E>();
    first.item = item;
    first.next = next;
    n++;
  }
  public E pop() {
    E item = first.item;
    first = first.next;
    n--;
    return item;
  }
  public E top() {
    if(isEmpty()) return null;
    return first.item;
  }
}
```

**Relative Question (Exercise 5 - Q.3)**

`rec_pop()` that removes all the elements from a `StackNode`

```java
public void rec_pop() {
  if(isEmpty()) return;
  pop();
  rec_pop();
}
```

### Queue API

| return type | method(_type_ parameter) | Description                                                |
| ----------: | :----------------------- | ---------------------------------------------------------- |
|        void | enqueue(_E_ item)        | Add element to the back of queue                           |
|           E | dequeue()                | Remove and return the first element from the queue         |
|           E | first()                  | Return the first element of the queue, without removing it |
|     boolean | isEmpty()                | Return whether the queue is empty                          |
|         int | size()                   | Number of elements in the queue                            |

- Assume `null` is returned from `first()` and `dequeue()` when stack is empty

### Linked list queue

```java
public class LinkedQueue<E> implements Queue<E> {
  private SinglyLinkedList<E> list = new SinglyLinkedList<E>();

  public LinkedQueue() { }

  public int size() { return list.size(); }
  public boolean isEmpty() { return list.isEmpty(); }
  public void enqueue(E element) { list.addLast(element); }
  public E first() { return list.first(); }
  public E dequeue() { return list.removeFirst(); }
}
```

---

## Lists and Iterators

**java.util.List**

- linearly ordered collection
- provides indexed access

|    method | Description                                                                                                                                                                 |
| --------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|    size() | Returns the number of elements in the list                                                                                                                                  |
| isEmpty() | Returns a boolean indicating whether the list is empty                                                                                                                      |
|    get(i) | Returns the element of the list having index i; IndexOutOfBoundsException if i not in [0, size()-1]                                                                         |
| set(i, e) | Replaces the element at index i with e, returns the old element that was replaced; IndexOutOfBoundsException if i not in [0, size()-1]                                      |
| add(i, e) | Inserts a new element e into the list so that it has index i, moving all subsequent elements one index later in the list; IndexOutOfBoundsException if i not in [0, size()] |
| remove(i) | Removes and returns the element at index i, moving all subsequent elements one index earlier in the list; IndexOutOfBoundsException if i not in [0, size()-1]               |

### Array Lists (bounded capacity)

- Implement List with array
- array A where A[i] stores a reference to the element with index i

|            method | Implementation                                                   |       TimeComplexity        |
| ----------------: | :--------------------------------------------------------------- | :-------------------------: |
| get(i), set(i, e) | Access on A[i]                                                   |            O(1)             |
| size(), isEmpty() | Access on `data.length`                                          |            O(1)             |
|         add(i, e) | Shift forward the elements A[i], ..., A[n-1], set A[i] as e      | O(n); Worst case: shift all |
|      remove(i, e) | Shift backward the elements A[i+1], ..., A[n-1], set A[n-1] as e | O(n); Worst case: shift all |

```java
public class ArrayList<E> implements List<E> {
  public static final int CAPACITY=16;
  private E[] data;
  private int size = 0;
  public ArrayList() { this(CAPACITY); }
  public ArrayList(int capacity) { data = (E[])new Object[capacity]; }

  public int size() { return size; }
  public boolean isEmpty() { return size == 0; }
  public E get(int i) throws IndexOutOfBoundsExcpetion {
    checkIndex(i, size);
    return data[i];
  }
  public E set(int i, E e) throws IndexOutOfBoundsException {
    checkIndex(i, size);
    E answer = data[i];
    data[i] = e;
    return answer;
  }
  public void add(int i) throws IndexOutOfBoundsException {
    checkIndex(i, size);
    if (size == data.length) { throw new IllegalStateException("Array is Full!"); }
    for (int k=size-1; k>=i; k--) { data[k+1]=data[k]; }
    data[i] = e;
    size++;
  }
  public E remove(int i, E e) throws IndexOutOfBoundsException {
    checkIndex(i, size+1);
    E answer = data[i];
    for (int k=i; k<size-1; k++) { data[k]=data[k+1]; }
    data[size-1]=null;
    size--;
    return answer;
  }
  protected void checkIndex(int i, int n) throws IndexOutOfBoundsException {
    if (i<0 || i>=n) { throw new IndexOutOfBoundsException("Illegal index: "+i); }
  }
}
```

### Dynamic Arrays (unbounded capacity)

**fixed maximum capacity** cause inefficient waste or easily exhausting capacity

&rarr; Dynamically adjust the size of the array

- if capacity is exhausted, requests a new, larger array
- copies all references from the smaller array into the beginning of the new array

**Doubling Strategy** double the size of the array when the array has been filled up

**Halving Strategy** half the size of the array when the size is less than 1/4

\* with these strategies, we can improve ArrayStack which had limited size problem

```java
public void add(int i) throws IndexOutOfBoundsException {
  checkIndex(i, size);
  if (size == data.length) { resize(2*data.length) }
  for (int k=size-1; k>=i; k--) { data[k+1]=data[k]; }
  data[i] = e;
  size++;
}
public E remove(int i, E e) throws IndexOutOfBoundsException {
  checkIndex(i, size+1);
  E answer = data[i];
  for (int k=i; k<size-1; k++) { data[k]=data[k+1]; }
  data[size-1]=null;
  size--;
  if (size>0 && size<data.length/4) { resize(data.length/2); }
  return answer;
}

protected void resize(int capacity) {
  E[] temp = (E[])new Object[capacity];
  for (int k=0; k<size; k++) { temp[k] = data[k]; }
  data = temp;
}
```

**java.util.ArrayList** implements all optional list operations

### Amortized Analysis of Dynamic Arrays

**Amortized** analysis: spread the cost of the few expensive operations, while keeping the avarage cost of operations low

**Push operation** takes different running time

- Worst case (doubling) takes O(n)
- Most case takes O(1)

  &rarr; for n=2^k, total running time of n push operations is T(n) = n+1+2+4+ ... +2^k=n+2^{k+1}-1=3n-1=O(n).

Thus, amortized running time of each push operation is O(1) in doubling-and-halving strategy

Similarly, pop operation takes worst O(n), amortized O(1)

**Relative Question (Quiz 1 - Q.3, Q.4)**

- Q3: increasing two cells per push / total running time of n push operations on an empty dynamic array
  - T(n)=n + 1+3+5+ ... +n=O(n^2): Quadratic
- Q4: double when full, half when half-full / worst-case running time of n push, pop operations on an empty dynamic array
  - Specific scenario
  - push n/2+1 which will made the array size n
  - pop will half the array
  - repeat push and pop then every operation will affect the size and take linear time
  - for n=2^k, T(n) = (n/2+1)+(1+2+4+ ... +n/2)+(n/4)\*((n/2+1)+(n/2))=O(n^2): Quadratic

### Iterators

**Iteration** is processing all of collections' items

- In Java, we make collection implement the `java.lang.Iterable`

**foreach** / two code fragments below are equivalent

```java
Iterator<type> iter = Iterable.Iterator();
while(iter.hasNext()) {
  type var = iter.next();
  ...
}
```

```java
for(type var: Iterable) { ... }
```

\* String is not "Iterable"

**Relative Question (Quiz 1 - Q.5)**: Fill the code block

**java.lang.Iterable** promise to provide an `iterator()` method
**java.util.Iterator** requires following methods

| Method    | Description                                  |
| --------- | -------------------------------------------- |
| hasNext() | returns whether iterator has next            |
| next()    | returns an item from the collection          |
| remove()  | optional; To filter a collection of elements |

```java
import java.lang.Iterable;

public class ArrayList<E> implements List<E>, Iterable<E> {
  ...
  @Override
  public Iterator<E> iterator() {
    return new ArrayIterator();
  }

  private class ArrayIterator implements Iterator<E> {
    private int j = 0;
    public boolean hasNext() { return j<size; }
    public E next() {
      if (!hasNext()) throw new NoSuchElementException();
      return data[j++];   // return data[j] and increase j
    }
    public void remove() { throw new UnsupportedOperationException(); }
  }
  ...
}
```

**Relative Question (Quiz 1 - Q.6)**

- Implement reverse iterator

```java
import java.util.Iterator;
import java.util.NoSuchElementException;

public class ArrayList<E> implements List<E>, Iterable<E> {
  public static final int CAPACITY=16;
  private E[] data;
  private int size = 0;

  ...

  public Iterator<E> iterator() { return __(1)__; }

  private class ArrayIterator implements __(2)__ {
    private int k = size-1;
    public boolean hasNext() { return __(3)__; }

    public E next() {
      if(!hasNext()) throw new NoSuchElementException();
      return __(4)__;
    }
    public void remove() { throw new UnsupportedOperationException(); }
  }
}
```

- (1) ArrayIterator (2) Iterator<E>
- Since `k` is given size-1, we can predict that (4) must return `data[k]` first and decrese `k`. Thus, (4) data[k--]
- Then, `hasNext()` is same with whether `k` is proper index, which means `k>=0`. Thus, (3) k>=0

---

## Tree

**Tree** is ADT that stores elements hierarchically: parent-child relation

- each element has a parent element and zero or more children elements
- only root has no parent

### Terminology

- **Root** node without parent
- **Internal node** node with at least one child
- **External node**(=**Leaf**) node without children
- **_Depth_ of a node** # of edges from root to node
- **_Level_ _d_ of a tree** set of all nodes of a tree at the same depth _d_
- **_Height_ of a tree** maximum depth of leaf nodes
  - Height of single-node tree is 0
  - Height of empty tree is -1
- **Subtree** tree consists of a node itself and all of its descendants
- **Siblings** nodes have same parent node
- **Ordered Trees** Tree with meaningful linear order among the children of each node

### Binary Tree

- Every node has at most two children
- Each child node is a left child or a right child
- A left child precedes a right child in the order of a children of a node
- Level _d_ has at most 2^d nodes
- Total number of nodes: n, height: h
  - h+1<= n <= 2^{h+1}-1

**Full Binary Tree** Each node has either zero or two children (= every internal node has exactly two children)
**Complete binary Tree** The nodes at level _h_ reside in the leftmost possible positions at that level

**General tree to Binary tree**: LCRS; Left Child Right Sibling

### Traversing a tree

**Traversal** The most basic tree-processing function

- **Preorder** node > left subtree > right subtree
- **Postorder** left subtree > right subtree > node
- **Inorder** left subtree > node > right subtree
- **Breadth-First** visit all nodes at depth d, repeat for d+1

### Binary Search Tree

- For each internal node _u_,
  - left subtree stores elements less than e(_u_)
  - right subtree stores elements greater than e(_u_)
- Inorder traversal of BST visits all nodes in ascending order

| Operation | Implementation                                               |
| --------- | ------------------------------------------------------------ |
| Search    | If less, go left; If greater, go right; If equal, search hit |
| Insert    | If less, go left; If greater, go right; If null, insert      |

- Running time of search is proportional to height of tree

### Implementation in Java

**Comparable** Interface based on the natural ordering

- Promise to provide `a.compareTo(b)` method, which returns an integer with following meaning:
  - i<0 &rarr; a<b
  - i=0 &rarr; a=b
  - i>0 &rarr; a>b
- If it is incompatible type or either is null, throws an exception

```java
public class BST<E extends Comparable<E>> implements Tree<E> {
  private static class Node<E> {
    private E element;
    private Node left;
    private Node right;
    private int n;  // node count in the subtree rooted at the node
    public Node(E e, int n) {
      element = e;
      this.n = n; // Not to confuse, specify this
    }

    public int getSize() { return n; }
  }

  private Node<E> root;

  public boolean search(E e) {
    Node<E> current = root;
    while(current != null) {
      int cmp = e.compareTo(current.element);
      if (cmp < 0) current = current.left;
      else if (cmp > 0) current = current.right;
      else if (cmp == 0) return true;
    }
    return false;
  }

  public void insert(E e) {
    root = insert(root, e);
  }

  private void insert(Node x, E e) {
    if (x==null) return new Node(e, 1);
    int cmp = e.compareTo(x.element);
    if (cmp < 0) x.left = insert(x.left, e);
    else if (cmp > 0) x.right = insert(x.right, e);
    else x.element = e;
    x.n = 1+getSize(x.left)+getSize(x.right);
    return x;
  }
}
```

**Inner class** is nonstatic nested class.

- Iterator class is inner class since its definition depends on size which is differ by instance

---

## Priority Queues

- A collection of prioritized elements that allows arbitrary element insertion, and allows the removal of the elment that has first priority (largest or smallest)

\* To avoid confusion, we usually have a seperate implementation of MinPQ and MaxPQ

- Easily converted each other

public class MaxPQ<Key extends Comparable\<Key\>\>

| Return type | Method         | Description                             | unordered array | ordered array |
| ----------: | :------------- | --------------------------------------- | --------------- | ------------- |
|             | MaxPQ()        | create an empty priority queue          |                 |               |
|             | MaxPQ(Key[] a) | create a priority queue with given keys |                 |               |
|        void | insert(Key v)  | insert a key into the priority queue    | O(1)            | O(N)          |
|         Key | delMax()       | return and remove the largest key       | O(N)            | O(1)          |
|     boolean | isEmpty()      | is the priority queue empty?            |                 |               |
|         Key | max()          | return the largest key                  | O(N)            | O(1)          |
|         int | size()         | number of entries in the priority queue |                 |               |

### (Binary) Heap

- Data structure that can efficiently support the basic priority-queue operations
- Complete binary tree property
- **heap-ordered** key in each node is larger than or equal to the keys in that node's two children
  - **Max-heap** a[k/2] >= a[k], **Min-heap** a[k/2] <= a[k]
- Array representation
  - 1-based indexing &rarr; simplifies arithmetic
  - Take nodes in level order
  - a[1]: root, a[2]: left child of root, a[3]: right child of root, ...
- Can use array indices to move through tree
  - Parent of node at _k_ is at _k/2_
  - Children of node at _k_ are at _2k_ and _2k+1_
  - Largest key is a[1]
- Consideration
  - Underflow: throw exception / Overflow: resizing array

### Algorithms on heaps

- Helper Method
  - Is item u(=pq[i]) less than w(=pq[j])?
  - Key must be `Comparable<Key>` to use `compareTo()`

```java
private boolean less(int i, int j) {
  return pq[i].compareTo(pq[j]);
}
```

- Swap item in array pq[] at index i with one at index j

```java
private void exch(int i, int j) {
  Key swap = pq[i];
  pq[i]=pq[j];
  pq[j]=swap;
}
```

- Reheapify
  - Bottom-up (swim up): O(log N)
    - When child becomes larger than parent
    - Exchange key in child with key in parent and repeat

```java
private void swim(int k) {
  while (k>1 && less(k/2, k)) {
    exch(k, k/2);
    k = k/2;
  }
}
```

- Top-down (sink down): O(log N)
  - When parent becomes smaller than at least one of children
  - Exchange key in parent with key in larger child and repeat

```java
private void sink(int k) {
  while (2*k<=N) {
    int j = 2*k;
    if (j<N && less(j, j+1)) j++;
    if (!less(k, j)) break;
    exch(k, j);
    k = j;
  }
}
```

- Implementation

```java
public void insert(Key x) {
  pq[++N] = x;
  swim(N);
}

public Key delMax() {
  Key max = pq[1];
  exch(1, N--);
  sink(1);
  pq[N+1] = null;
  return max;
}
```

| insert() | delMax() | max() |
| -------- | -------- | ----- |
| O(logN)  | O(logN)  | O(1)  |

### Heapsort

1. Heap construction: Create a max-heap with all _n_ keys using bottom-up method from the last element of heap
   - Assume that n=2^k. Then the height of tree is k.
   - For each subheap with height h, it compares h time.
   - Number of subheap with height h is 2^{k-h}.
   - Thus, total running time of heap construction is k+2(k-1)+ ... +2^{k}(k-k)=2^{k+1}-1-(k+1)=O(n)
2. Sortdown
   - Repeatedly remove the maximum key
   - Move it to last position in the array. Since heap shrinks, it is not included in heap.
   - `sink()` to reheapify
   - jth sink takes O(log(N-j+1)). Thus it totally takes O(nlogn)

**Relative Question (Quiz 2 - Q.5)**

---

## Maps & Hash Tables

### Map

- models a searchable collection of key-value pair abstraction with all different keys
- No duplicate keys, no null keys, no null values
- Keys are comparable
- No limit on number of key-value entries
- Java has three concrete classes: HashMap, LinkedHashMap, TreeMap

|     Method | Description                                                                                                                                                                                        |
| ---------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|     size() | Returns the number of entries in M                                                                                                                                                                 |
|  isEmpty() | Returns whether M is empty                                                                                                                                                                         |
|     get(k) | Returns the value v associated with key k, if such an entry exist; otherwise returns null                                                                                                          |
|  put(k, v) | if M does not have an entry with key equal to k, then adds entry (k, v) to M and returns null; else, replaces with v the existing value of the entry with key equal to k and returns the old value |
|  remove(k) | Removes from M the entry with key equal to k, and returns its value; if M has no such entry, then returns null                                                                                     |
|   keySet() | Returns an iterable collection containing all the keys stored in M                                                                                                                                 |
|   values() | Returns an iterable collection containing all the values of entries stored in M (with repetition if multiple keys map to the same value)                                                           |
| entrySet() | Returns an iterable collection containing all the key-value entries in M                                                                                                                           |

### Implementation

**unordered linked list**

- Search: Scan through all keys until find a match (sequential search): O(n)
- Insert: Scan through all keys until find a match; if no match add to front: O(n)

**ordered array**

- Parallel array between keys array and values array
- Search: Binary search on keys array: O(log n)
- Insert: Have to shift at most all: O(n)

### Hashing functions

- **Hash function** Method for computing array index from key
  - **Hash code** Map a key k to an integer
  - **Compression function** Map hashccode to a hash value (an integer within a range of indices, [0, N-1])
- Uniform Hashing Assumption
  - Hash functions uniformly and independently distribute keys among the integer values in [0, N-1]

**Compression function**

- Division Method
  - `key.hashCode() % N` or `Math.abs(key.hashCode()) % N`
  - take N be a prime number helps 'spread out' the distribution
  - For minimum integer(-2^31) as hashcode, it cannot be mapped into [0, M-1] since it is larger than maximum integer.
  - `(key.hashCode() & 0x7fffffff) % M` would be okay
    - Two's complement

### Collision Resolution

**Collisions** Two distinct keys hashing to same index

**Seperate chaining symbol table**

- Use an array of M linked lists, where M<N
  - Hash: Map key to integer in [0, M-1]
  - Insert: put at front of its chain if not already there
  - Search: search along the chain
- If we have m lists and n keys, average length of the lists a = n/m, which is referred as **load factor**
- With uniform hashing assumption, every key is equally likely to be hashed to one of m indices. In other words, length of chains can be assumed as load factor.
  - insert / search average takes O(a)=O(1)

```java
public class SeperateChainingHashST<Key, Value> {
  private Node[] st;
  private static class Node {
    private Object key;
    private Object val;
    private Node next;
  }

  private int hash(Key key) { return (key.hashCode() & 0x7fffffff) % N; }
  public void put(Key key, Value val) {
    int i = hash(key);
    for (Node x = st[i]; x != null; x = x.next) {
      if (key.equals(x.key)) { x.val = val; return; }
    }
    st[i] = new Node(key, val, st[i]);
  }
}
```

**Open addressing** find next empty slot, put it there

- **Linear Probing** [h(x) + i] mod M for i= 1,2,3,…
  - Clustering
- **Quadratic Probing** [h(x) + i^2] mod M for i= 1,2,3,…
  - Secondary clustering
- **Double Probing** [h(x) + i* h'(x)] mod M for i= 1,2,3,…
  - More difficult to implement the delete operation

### Set

- unordered collection of elements without duplicates
- map without values
- java.util.HashSet

---

## Search Trees

### BST

- binary tree in symmetric order
- Removal
  - To remove a node with a given key
    - Set its value to null / Leave key in tree: guide search, not consider as equal
      - memory overload
    - Replace node with its successor (leftmost child of right subtree) / right link of successor will be left link to successor's parent
      - it is okay to use predecessor
  - To remove minimum key
    - Search leftmost node
    - Replace the link to that node by its right link
    - Update subtree counts
- Insert
  - Shape of tree depends on insertion order
  - get/put/remove take O(h) times where h is height of tree
    &rarr; need to be balanced

### Balanced Search Trees

**AVL tree** BST satisfies the height-balance property

- height-balance property: the heights of the children of every internal node differ by at most 1
- balance factor: height(right subtree) - height(left subtree)
- Balancing after inserting / deleting
  - Rotation: Attach child to parent and rotate
  - LL case: single right rotation
  - RR case: single left rotation
  - LR case: left - right rotation
  - RL case: right - left rotation

**2-3 tree**

- 2-node: one key, two children / 3-node: two keys, three children
- Implementation is complicated
- Search
  - Compare search key against keys in node
  - Find interval containing search key
  - Follow associated link (recursively)
- Insertion
  - To 2-node: replace into 3-node
  - To 3-node: temporarily create 4-node, move middle key in 4-node into parent

---

## Sorting

### Comparator

- Promise to provide `compare()` method

### Stability

- Whether the relative order of items with equal keys preserved or not

### Selection Sort

- i: pointer / min: index of minimum item in [i, a.size()-1]
- Quadratic time, Linear exchanges
- unstable

### Insertion Sort

- i: pointer / j: place where pointing item will inserted
- Quadratic Time, Quadratic exchanges
- stable

### Merge Sort

- lo: leftmost index / hi: rightmost index / mid: rightmost index of left subarray
- stable

**Top-down** Divide and Merge

- ex) 20 &larr; 10/10 &larr; 5/5/5/5 &larr; 3/2/3/2/3/2/3/2 &larr; 2/1/1/1/2/1/1/1/2/1/1/1/2/1/1/1 &larr; 1/1/1/1/1/1/1/1/1/1/1/1/1/1/1/1/1/1/1/1/1

**Bottom-up** Partially sort and merge

- `int lo=0; lo<N-sz; lo += sz+sz`
- ex) 20 &larr; 16/4 &larr; 8/8/4 &larr; 4/4/4/4/4 &larr; 2/2/2/2/2/2/2/2/2/2

### Quick Sort

- i: index from left, larger than pivot / j: index from right, smaller than pivot
- unstable
