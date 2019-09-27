---
title: smileDemo
date: 2019-06-29 10:59:55
tags:
- translate
category:
- okkkkk
- 89821931
---




##### ES5中继承的实现：
```shell
//ES5中的思路是将子类的原型设置成为父类的原型
function Super(){
	Super.prototype.getNum = function(){
		return 1;
	}
}
function Sub(){

}

	let s = new Sub();
	Sub.prototype = Object.create(Super.prototype,{
		constructor:{
			value:Sub,
			writeable:true
		}
	})
```
###### 另外案例：
```shell
// Shape - 父类(superclass)
function Shape() {
  this.x = 0;
  this.y = 0;
}

// 父类的方法move
Shape.prototype.move = function(x, y) {
  this.x += x;
  this.y += y;
  console.info('Shape moved.');
};

// Rectangle - 子类(subclass)
function Rectangle() {
  Shape.call(this); // call super constructor.
}

// 子类续承父类；子类的prototype指向父类的prototype

Rectangle.prototype = Object.create(Shape.prototype);
Rectangle.prototype.constructor = Rectangle;

//实例化子类对象
var rect = new Rectangle();

console.log('Is rect an instance of Rectangle?',
  rect instanceof Rectangle); // true
console.log('Is rect an instance of Shape?',
  rect instanceof Shape); // true
rect.move(1, 1); // Outputs, 'Shape moved.'
```
###### Object.create()方法创建一个新对象，其作用是使用现有的对象来提供新创建的对象的__proto__，语法：
`Object.create(proto[, propertiesObject])`

##### ES6中直接用class ... extends即可
```shell
class MyDate extends Date(){
	test(){
		return this.getTime();	
	}
}
let myDate = new MyDate();
myDate.test();
```

