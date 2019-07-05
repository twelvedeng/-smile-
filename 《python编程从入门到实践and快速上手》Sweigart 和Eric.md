#### 【第一二章】

- elif语句等于 else if语句（但在python里没有else if）

- def 自定义函数 函数的参数在函数返回后就消失了没法继续使用

- str函数 传入int 转换成string类型

- 整型值可以与浮点值相等

- sys.exit ()提前结束程序  

- 常见except:

  1. IndexError
  2. ValueError
  3. ZeroDivisionError
  4. TypeError

- for循环和range函数合用：

  ```python
  for i in range (a,  b):   #循环变量i从a到b递增1执行（不包括b 
  for i in range (a,  b, c):  #从a到b，循环变量i每次加c
  ```

#### 【第三章 函数】

1. 函数包括def语句及在def语句中的代码。函数调用让函数执行转到函数内，函数调用求值为该函数的返回值。

2. 调用函数时，创造了一个全局函数和局部作用域。

3. 如果函数没有返回值，它就返回None（数据类型是NoneType，相当于其他语言里的NULL)。

4. global语句强制函数中一个变量引用该全局变量。

5. 可能导致错误的语句放在try子句中，发生错误时要执行的语句放在except子句中。如：

   ```python
   try:
   	n = int(input())
   except ValueError:
       print('Error: u have to enter an integer!')
   ```

6. print()函数有可选的变元end和sep，分别指定在参数末尾打印什么，以及在参数之间打印什么来隔开他们。

   ```python
   >>> print('hello')
   >>> print('world')
   hello
   world
   >>> print('hello', end = '')
   >>> print('world')
   helloworld
   ```

   ```python
   >>> print('cookie', 'summer', 'swim')
   cookie summer swim
   >>> print('cookie', 'summer', 'swim', sep = ',')
   cookie,summer,swim
   ```

#### 【第四章 列表】

**{列表基本}**

1. 有负数下标，-1表示最后一个数，-2倒数第二个，以此类推。

2. 切片：可以当列表用，spam[1, 4]  //前一个数为开始时下标，后一个数为结束时下标（不包括这个数，如：

   ```python
   spam = ['a', 'b', 'c' ,'d']
   spam[1, 3] = ['b', 'c']
   spam[0, -1] = ['a', 'b', 'c']
   ```

3. len()可取列表长度； +可连接列表； *可用于一个列表和整数，实现列表的复制；（和字符串像的性质，+=也可

4. 使用range()创建数字列表

   ```python
   numbers = list(range(1, 6))
   
   #将前十个整数的平方加入一个列表
   squares = []
   for value in range(1,11):
       square = value**2
       squares.append(square)
       #前两行可squares.append(value**2)
       
   #列表解析
   squares = [value**2 for value in range(1,11)]
   ```

   

5. del语句从列表中删除值（改变了列表长度）

   ```python
   >>> spam = ['c', 'b']
   >>> del spam[0]
   >>> print(spam)
   spam = ['b']
   ```

   当del用于简单变量时，等价于‘取消赋值’，把变量的地址也一起删除了（但这个操作基本用不上）

6. for循环遍历输出可以用range(len(somelist))

   ```python
   for i in range(len(somelist)):
       print(somelist[i])
   ```

7. in和not in判断是否存在一个值x在列表中，返回bool值

   ```python
   >>> spam = ['hello', 'hi', 'blackberry']
   >>> 'hi' in spam
   True
   >>> 'swim' in spam
   False
   #bool值记得首字母大写
   ```

8. 列表中缩进不重要，在没有右方括号的时候就代表列表没有结束。

9. 行末可用续行字符+\

   ```python
   >>> print('Four score and seven '+\
            'years ago.')
   Four score and seven years ago.
   ```

**{其他}**

列表是可以修改的，他们可以添加、删除、修改值。元组是不可以修改的，他们根本不能被改变。元组使用(),列表使用[]。当要进行类型转换时使用list()和 tuple()函数

```python
>>> tuple(['xi', 5])
('xi', 5)
>>> list（('xi', 6)）
['xi', 5]
>>> list('xi')
['x', 'i']
```

想要改变一个字符串列表的大小写并且保存到列表时

```python
current = ['hapPY', 'Log', 'Milk']


#只是输出小写时
for cur in current:
    print(cur.lower()， end = ', ')
结果：happy, log, milk

#错误做法(该做法只在循环内改变了值，改变的值没有存入列表，不能通过列表使用)
for cur in current:
    cur = cur.lower()
print(current)
结果：['hapPY', 'Log', 'Milk']

#创建新的列表保存
now = []
for cur in current:
    now.append(cur.lower)
    
#使用原来的列表
for index in enumerate(current):
    
    
```

当元组只有一个整数值42时，如何输入该元组

```python
#末尾的逗号时必须的
>>> (42,)
```

**{列表方法}**

1. index()查询：返回列表中值的下标，当知道值的时候返回地址（值重复时返回它第一次出现的下标）

2. append(), insert()插入：append添加元素到列表末尾，返回值为None；insert添加元素到任意下标。

   ```python
   >>> spam = ['cats', 'dogs', 'sun']
   >>> spam.insert(1, 'chicken')
   >>> spam
   ['cat', 'chicken', 'dogs', 'sun']
   ```

3. remove()删除：多次出现时删除出现的第一次，知道要删除元素下标时用del子句，不知道时用remove。

4. sort()排序：默认从小到大排序，使用reverse和True可以逆序（从大到小

   ```python
   >>> spam.sort(reverse = True)
   >>> spam
   ```

   不能对元素既有字母又有数字的列表进行排序，会有TypeError。

   sort对字符类型排序时按“ascii字符顺序”，所以大写排在小写前面，如果想要让它们按字典序排列的话，引入key和str.lower

   ```python
   >>> spam = ['a', 'z', 'A', 'Z']
   >>> spam.sort(key = str.lower)
   >>> spam
   ['a', 'A', 'z', 'Z']
   ```

5. copy模块：copy()f复制列表或字典这样的可变值，而不只是复制引用

   \deepcopy()深拷贝列表，复制列表内的所有列表
   
   

#### 【第五章 if语句】



#### 【其他】

##### {字典}

字典：
    格式 变量名 = {key:val,key:val}
    字典的键 必须是不可变的数据类型,而且键不能重复 值可以是任意类型
    字典是无序

访问字典：
    通过键直接访问 变量名[key]   如果键不存在会报错
    通过 get(key,[指定的值]) 方法 访问 如果键不存在返回None不会报错 如果指定的值 返回指定的值 

```python
修改字典的值和添加：
     通过键重新赋值 变量名[key] = value  如果键存在就修改 如果键不存在就添加
     setdefault({})   如果键不存在就添加
     update(key,value)  如果键存在就修改 不存在就添加

 删除字典中的值：
    pop(key)  弹出指定键对应的值  返回弹出键对应的值       
    popitem()   随机弹出一个键  返回 一个由键和值组成的元组
    clear()     清空字典
    del         删除指定的键 或之间删除变量

 函数：
    keys()   返回所有的键
    values()   返回所有的值
    items()    返回所有的键和值  
```
字典的遍历：
    遍历所有的键
    遍历所有的键和值