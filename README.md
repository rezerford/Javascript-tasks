# Javascript-tasks

**1. Напиши функцию создания генератора sequence(start, step). Она при вызове возвращает другую функцию-генератор, которая при каждом вызове дает число на 1 больше, и так до бесконечности. Начальное число, с которого начинать отсчет, и шаг, задается при создании генератора. Шаг можно не указывать, тогда он будет равен одному. Начальное значение по умолчанию равно 0. Генераторов можно создать сколько угодно.**

```
var generator = sequence(10, 3);
var generator2 = sequence(7, 1);

console.log(generator()); // 10
console.log(generator()); // 13

console.log(generator2()); // 7

console.log(generator()); // 16

console.log(generator2()); // 8
```

**Решение**

```
function sequence(start, step){
  
  var i = i || 0;
  var number = number || start;
   
  return function(){
    
    if(i)
      number += step;
    
    i++;
    return number;
    
  }
}
```

**2. Также, нужна функция take(gen, x) которая вызвает функцию gen заданное число (x) раз и возвращает массив с результатами вызовов. Она нам пригодится для отладки:**

```
var gen2 = sequence(0, 2);
console.log(take(gen2, 5)); // [0, 2, 4, 6, 8 ]
```

**Решение**

```
function take(func, count){
 
  var arr = [];
  
  for(var n = 0; n < count; n += 1){
      
    var j = func();
    arr.push(j);
    
  }
  
  return arr;
  
}

var gen2 = sequence(0, 2);
console.log(take(gen2, 15));
```

**3. Напиши функцию map(fn, array), которая принимает на вход функцию и массив, и обрабатывает каждый элемент массива этой функцией, возвращая новый массив. Пример:**

```
function square(x) { return x * x; } // возведение в квадрат
console.log(map(square, [1, 2, 3, 4])); // [1, 4, 9, 16]
console.log(map(square, [])); // []
```

**Обрати внимание: функция не должна изменять переданный ей массив:**

```
var arr = [1, 2, 3];
console.log(map(square, arr)); // [1, 4, 9]
console.log(arr); // [1, 2, 3]
```

**Это аналог array_map из PHP.**

**Решение**

```
function map(func, arr){
   
  if(!(func instanceof Function)){
    
    throw "First argument is not a function";
    return false;
  }
  
  if(!(arr instanceof Array)){
    
    throw "First argument is not an array";
    return false;
  }
  
  var return_arr = [];
  
  for(var n = 0, len = arr.length; n < len; n += 1){
    
    var j = func(arr[n]);
    return_arr.push(j);
    
    
  }
  
  return return_arr;
  
}

var func = function(x){ return x*x; };
var arr = [1,2,3,4];

console.log(map(func, arr));
```
