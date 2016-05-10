## Syllabus

### Using the Python Interpreter
#### Argument Passing
The python script name and additional arguments thereafter are turned into a list of string and assigned into argv variable in sys module.

* When no script and no argument:
	`sys.argv[0]` is an empty string
* When script name is given as -:
	`sys.argv[0]` is set to "-"
* When `-c` or `-m` command is used:
	`sys.argv[0]` is set to `-c` or `-m` respectively


`python -c 'print(hello world)'`

Here `-c` stands for a python command
Anything written after `-c` must be a valid python command

`python -m pdb python-101.py`

`-m` stands for module
`pdb` stands for python debugger
`python-101.py` is a file containing the python code

`python -i python-101.py`

`-i` means, python will run the program, `python-101.py` and dump you into 
interactive interpreter 
It helps in monitoring the variables at the end of the program.

To enter directly into python interpreter just type:
`python`

Another way using python interpreter: 
Create a file named foo.py

The content of the file foo.py:
```python
#!/usr/bin/env python

print("This is python-101")
``` 
There are two ways to run this file:
* `python foo.py`
* Make it executable `chmod +x foo.py` and run the executable `./foo.py`

### Introduction to Python

#### Numbers
##### +, -, * and /

These operator works similar to other languages. 
```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # division always returns a floating point number
1.6
```

* `/` always returns a float.
* `//` can be used to discard the fractional part
* `%` can be used to calculate the remainder
* `**` is used to calculate powers
* `=` is used to assign a value to a variable

```python
>>> 12 ** 2
144
>>> 2 ** 3
8 
```

##### Variable assignment:

```python
>>> a = 12
>>> b = 14
>>> a + b
26
>>> c = a + b
>>> c
26

```

In interactive mode the last printed expression is assigned to a variable named `_`

#### Strings

* Strings can be enclosed in single quotes (`'...'`)or double quotes(`"..."`).
* `\` Can be used for escaped characters
* We can use a combination of single quotes and double quotes to avoid use of `\` before escaped character

```python
>>> 'This is BangPypers'
'This is BangPypers'
>>> 'Rama don\'t like python'
'Rama don't like python'
>>> "Hari don't know why"
"Hari don't know why"
```
* `print()` function omits the enclosing quotes.

```python
>>> print("Hari loves python")
Hari loves python

```
* If you want to print the string as it is without interpreting prefaced `\` as a special character then use raw strings 

```python
>>> print('home\abc')
homebc
>>> print(r'home\abc')
home\abc
```

* If string is too long use triple quotes, `("""...""" or '''...''')`

```python
>>> print(""" Python is very easy
... I am learning python 
... It is a beautiful language """)
Python is very easy
I am learning python 
It is a beautiful language 
>>> 
``` 
* Strings can be concatenated using `+` and repeated with `*`

```python
>>> "p" + "y" * 5 + "thon"
'pyyyyython'

```
* Two or more string literals, next to each other are automatically concatenated.
* To concatenate a string literal and a string variable we must use `+`

```python
>>> "hello" "world"
'helloworld'
>>> var = "abc"
>>> var + "def" 
'abcdef'
>>> var "def"  # This will give syntax error
File "<stdin>", line 1
var "def"
^
SyntaxError: invalid syntax

```

##### String Indexing

* First character of a string has index 0
* Character is a string of size 1
* If index is a negative number, it starts counting form the right
* Negative indices start form -1

```python
>>> word = "This is Python Bangpypers"
>>> word[0]  # Indexing starts from 0
'T'
>>> word[1]
'h'
>>> word[5]
'i'
>>> word[12]
'o'
>>> word[-1] # -ve indexing starts form -1 and it points to last character
's'
>>> word[-2]
'r'
>>> word[-5]
'y'
>>> 

```

* To obtain substring we use word slicing
* In `word[2:10]`, character at index `2` is included and at index `10` is excluded
* Slices have default indices. An omitted first index defaults to `0` and omitted 2nd index defaults to size of the string

```python
>>> word[15:-1]   # -ve index also works in slicing 
'Bangpyper'
>>> word[15:]     # last index defaults to length of the string
'Bangpypers'
>>> word[1:]        
'his is Python Bangpypers'
>>> word[:]       # First index defaults to 0
'This is Python Bangpypers'
>>> word[0:5]      
'This '

```

* Python strings are immutable 

```python
>>> word[5] = 'a'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment

```

##### String Methods
* `capitalize()`: Return a copy of the string with its first character capitalized and the rest lowercased
* `center(width[, fillchar])`: Return centered in a string of length width
* `count(sub[, start[, end]])`: Return the number of non-overlapping occurrences of substring sub in the range [start, end]
* `find(sub[, start[, end]])`: Return the lowest index in the string where substring sub is found
* `format()`: Returns a copy of the string where each replacement field is replaced with the string value of the corresponding argument.

```python
>>> "The sum of 1 + 2 is {0}".format(1+2)
'The sum of 1 + 2 is 3'
``` 
* `isalnum()`: Returns true if the string is alphanumeric
* `isalpha()`, `isdecimal()`,`isdigit()`, or `isnumeric()`
* `join()`: Return a string which is the concatenation of the strings, passed as argument in join. 

```python
#!/usr/bin/python

s = "-";
seq = ("a", "b", "c"); # This is sequence of strings.
print s.join( seq )
```
* `split`: The method split() returns a list of all the words in the string, using str as the separator optionally limiting the number of splits to num.

```python
#!/usr/bin/python

str = "Line1-abcdef \nLine2-abc \nLine4-abcd";
print str.split( )
print str.split(' ', 1 )

output:

['Line1-abcdef', 'Line2-abc', 'Line4-abcd']
['Line1-abcdef', '\nLine2-abc \nLine4-abcd']
```
* There are many other predefined methods for strings, see [here](https://docs.python.org/3/library/stdtypes.html#string-methods)

##### String Formating printf-style
See the examples below

```python
>>> print("My name is %s, I am %d yrs old" %("rajiv", 15))   # As tuples 
My name is rajiv, I am 15 yrs old
>>> print('%(language)s has %(number)03d quote types.' %     # As dictionary
...       {'language': "Python", "number": 2})
Python has 002 quote types.
```

##### in and len()
* `len(str)`: This will return the length of the string, `str`
* `"abc" in str`: Will return `true` if "abc" is substring of `str`

`str` is a string variable

### Data Structures

#### Lists

* Comma separated values between square brackets
* Lists can also be indexed and sliced
* List also support concatenation by `+`
* Lists are mutable
* To add items at the end of the list use `append()`

```python
>>> x = [1, 2, 3, 4, 5, 6]
>>> x
[1, 2, 3, 4, 5, 6]
>>> x[0]                        # indexing returns the item
1
>>> x[4]                        # indexing returns the item
5
>>> x[-1]                        # indexing returns the item
6

>>> x[2:]                        # Slicing returns a new list
[3, 4, 5, 6]

>>> x + [12, 13, 14]             # list support concatenation
[1, 2, 3, 4, 5, 6, 12, 13, 14]

>>> x[4] = 1000                  # lists are mutable
>>> x
[1, 2, 3, 4, 1000, 6]

>>> x.append("Bangalore")        # Will append bangalore at the end of the list
>>> x
[1, 2, 3, 4, 1000, 6, 'Bangalore']

>>> x[2:4] = ["Python"]          # Slices can also be initialized
>>> x                            
[1, 2, 'Python', 1000, 6, 'Bangalore'] #Lists do not have to hold the same data type

>>> len(x)                       # length of list can be found using len 
6


>>> ### Nesting of list
... 
>>> 
>>> a = [1, 2, 3]
>>> b = ["m", "n", "o"]
>>> nlist = [a, b]
>>> nlist
[[1, 2, 3], ['m', 'n', 'o']]
>>> nlist[0]
[1, 2, 3]
>>> nlist[1]
['m', 'n', 'o']
>>> nlist[1][0]
'm'
>>> nlist[0][2]
3


```

##### List Methods
* list.append(x): Add an item, `x` to the end of the `list`
* list.extend(L): Append the list, `L` to `list`
* list.insert(i, x): Insert item, `x` at index, `i` in the given `list`
* list.remove(x): Remove item, `x` from the `list`
* list.pop(i): remove an item at ith position from the list and return that value. If no index given it returns the last item.
* list.clear(): removes all items form the list
* list.index(x): index of item, `x` in the list
* list.count(x): returns the number of times item, `x` appears in the list
* list.reverse(): reverse the elements in the list in place
* list.copy(): returns a copy of the list
* list.sort(reverse=false): sort the list in ascending order if `reverse` is false and vice versa

##### The `del` statement
```python
>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> del a[0]                  # delete an item at ith index
>>> a
[1, 66.25, 333, 333, 1234.5]
>>> del a[2:4]                # delete sublist 
>>> a
[1, 66.25, 1234.5]
>>> del a[:]                  # delete whole list
>>> a
[]
>>> del a                     # delete the entire variable

The range() command is a convenient way to make sequential lists of numbers:

>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
Note that range(n) starts at 0 and gives the sequential list of integers less than n. If you want to start at a different number, use range(start,stop)

>>> range(2,8)
[2, 3, 4, 5, 6, 7]
The lists created above with range have a step of 1 between elements. You can also give a fixed step size via a third command:

>>> evens = range(0,20,2)
>>> evens
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
>>> evens[3]
6

len(evens)
```

#### Tuples

* All tuples are enclosed in paranthesis, to support nested tuples
* But input may or may not be surrounded by parenthesis
* Tuples are immutable
* But they can contain mutable objects, i.e. lists
* Empty tuples are created by empty pair of parenthesis
* Singleton tuples are created by having tuple value followed by a comma.
* `t = 12345, 54321, 'hello!'` is called `tuple packing`
* the reverse is `tuple unpacking` i.e. `x, y, z = t` .

```python
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
>>> # Tuples are immutable:
... t[0] = 88888
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> # but they can contain mutable objects:
... v = ([1, 2, 3], [3, 2, 1])
>>> v
([1, 2, 3], [3, 2, 1])
```

```python
>>> empty = ()
>>> x = 'hello',    
>>> len(empty)
0
>>> len(x)
1
>>> x
('hello',)
```

#### Dictionaries
* Called associative arrays in other languages
* They are indexed by user defined keys
* Keys are immutable
* Keys can only be strings and numbers
* Tuples can also be used as keys if they contain only strings and numbers
* Any mutable object cannot be used as a key, e.g lists, slices etc
* Dictionaries can be defined as unorderd set of "key, value" pairs
* it is possible to delete a "key, value" pair using del key
* `list(d.keys())` returns the list of keys of dictionary `d`
* `sorted(d.keys())` to get the keys in sorted order
* to check if `key` is present in dictionary we can use `in` keyword

Some examples

```python
>>> score = {'harry': 75, 'snape': 97}
>>> score['ron'] = 50
>>> score
{'snape': 97, 'ron': 50, 'harry': 75}
>>> score['harry']
75
>>> del score['snape']
>>> score['voldemort'] = 60
>>> score
{'ron': 50, 'voldemort': 60, 'harry': 75}
>>> list(score.keys())
['voldemort', 'ron', 'harry']
>>> sorted(score.keys())
['ron', 'voldemort', 'harry']
>>> 'ron' in score
True
>>> 'harry' not in score
False
```

### Control Flow Tools

#### while loop
Lets see this with the help of an example

```python
>>> # first n Fibbonaci numbers
>>> n = 20               # single assignment
>>> a, b = 0, 1          # multi assignment 
>>> while n > 0:
    print(a)
    a, b, n = b, a+b, n-1         # multi assignment
... 
0
1
1
2
3
5
8
13
21
#deleting the rest.
```

###### To Note here apart form syntax of while 
* we can assign variables in the same line as shown in above example
* `print` is printing each output in different lines

##### Conditions in python
* any non-zero integer value evaluates to `true` and zero is `false`
* condition can also be a string or list value (anything with non-zero length is `true`)
* Empty list, string or any sequence is false
* standard comparison operators are: `<, >, ==, <=, >=, and !=`

##### More about print statement
* you can print any number of values using print statement followed by end of line

```python
>>> a, b = 10, 12
>>> print("value of a is: ", a, "value of b is: ", b)
value of a is:  10 value of b is:  12

```

* To avoid end of line use the  keyword argument `end `.

```python
>>> a, b = 0, 1
>>> while b < 1000:
    print(a, end=',')
    a, b = b, a+b
...
0, 1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
```

#### if Statement

See the example below
```python
>>> # Program to find if number is multiple of 2 or 3
... 
>>> x = int(input("Please enter an integer number: "))
Please enter an integer number: 56
>>> if x%2 == 0:
    print("x is a multiple of 2")
elif x%3 == 0:
    print("x is a multiple of 3")
else:
    print("x is not a multiple of 2 or 3")
... 
x is a multiple of 2
```

##### Note
* There can be zero or more `elif` block and `else` block is optional

##### input()
* Input is taken as a raw string which is then typecasted into its respective type.

#### for Statements

See the example below to understand about `for` statement in python 

```python
>>> ## To capitalize each statement in a string
... stringList = ["ravi got  his pocket money.", 
                  "he decided to buy an ice cream.", 
                  "he ran to the ice ream shop, but in hurry he forgot the money",
                  "ravi came back home and kept the money in his piggy bank"]
>>> for str in stringList:
...     print(str.capitalize())
... 
Ravi got  his pocket money.
He decided to buy an ice cream.
He ran to the ice cream shop, but in hurry he  forgot the money
Ravi came back home and kept the money in his piggy bank

```

* If the sequence itself needs to be modified while looping then its recommended to create a copy of same sequence using slice. 

```python
>>> for w in words[:]:  # Loop over a slice copy of the entire list.
...     if len(w) > 6:
...         words.insert(0, w)
...
>>> words
['defenestrate', 'cat', 'window', 'defenestrate']
```

##### Looping over integers
* Use `range()` function
* `range()` can be used in three ways
* `range(n)`: will contain numbers form `0` through `n-1`
* `range(x, y)`: will start from `x` and end at `y - 1`
* `range(x, y, z)`: will start at `x` and continue as `x + z`, `x + 2z` until `x + kz` is less than `y`

```python
range(5, 10)
   5 through 9

range(0, 10, 3)
   0, 3, 6, 9

range(-10, -100, -30)
  -10, -40, -70
```

To iterate over indices of a sequence

```python
>>> days_of_the_week = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"]
>>> for day in days_of_the_week:
    statement = "Today is " + day
    print statement
>>> for day in days_of_the_week:
    statement = "Today is " + day
    print statement
    if day == "Sunday":
        print "   Sleep in"
    elif day == "Saturday":
        print "   Do chores"
    else:
        print "   Go to work"
        
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
     print(i, a[i])
...
0 Mary
1 had
2 a
3 little
4 lamb
```

To iterate over dictionary
```python
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
     print(k, v)
...
gallahad the pure
robin the brave
```

```python
>>> for i in range(20):
    print "The square of ",i," is ",i*i
    
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
```

* To convert `range` into a list use `list(range(5))`

#### pythons `break` `continue` and `else`
* `break`: breaks out of the loop
* `continue`: continues with the next iteration of the loop
* `else`: It is executed when loop terminates through exhaution of the list (in case of `for`) or when loops condition becomes false (in case of `while`)

```python
>>> for n in range(2, 10):
...     for x in range(2, n):
...         if n % x == 0:
...             print(n, 'equals', x, '*', n//x)
...             break
...     else:
...         # loop fell through without finding a factor
...         print(n, 'is a prime number')
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

### Functions

#### Defining functions

Keyword `def` is used to create new  function.

```python
>>> def sum_n(n):
...     """ Prints sum of n natural numbers. """
...     print(n * (n + 1) / 2)
...
```

`def` is followed by function name `sum_n`, followed by arguements in parens `n`.

Statements followed by definition form body of function and they should be indented properly.

It can also have doc string to summarize what a function does. This is optional.

You can check whether an object is a function.

```python
>>> type(sum_n)
<class 'function'>
```

Calling a function with approriate arguements executes the function.

```python
>>> sum_n()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sum_n() missing 1 required positional argument: 'n'
>>> sum_n(5)
15.0
```

Functions are objects. They can be passed around just like variables.

```python
>>> add_n = sum_n
>>> add_n(5)
15.0
```


#### Return statement

Every function returns some value.

If user doesn't return any value, `None` will be returned.

```python
>>> x = sum_n(5)
15.0
>>> print(x)
None
```

Values can be returned from function using `return` statement.

We can modify previous function to return value instead of printing it.

```python
>>> def sum_n(n):
...     """ Returns sum of n natural numbers. """
...     return (n * (n + 1) / 2)
...
>>> x = sum_n(5)
>>> print(x)
15.0
```

#### Function arguments

Arguements can be either positional or keyword.


```python
>>> def fn(x, y):
    return  x+y
>>> fn(6,2)
8
>>> power(x=4,y=7)
11
```

We can assign default values to arguements to make them optional.

```python
>>> def fn(x=4, y=5):
...     return  x+y
...
>>> fn()
>>> fn(2)
>>> fn(3,6)
>>> fn(y=10)
```

### Check if number passed is prime or not
```python
def prime(n):
	"""Check if the given number is prime or not"""
	for i in range(2,n):
	    if n%i==0:
	        return False
	return True
```

### Lets try Fibonacci series
```python 
def fibonacci(n):
    "Return the Fibonacci sequence of length *n*"
    a,b=0,1
    if n < 1:
        print "Fibonacci sequence only defined for length 1 or greater"
        return
    for i in range(n):
	print a
	a,b=b,a+b
```

#### Builtin functions

Python has some builtin functions which are always available.


```python
>>> score = [45, 67,  89, -12]
>>> sum(score)
189
>>> len(score)
4
>>> max(score)
89
>>> min(score)
-12


>>> range(5)
range(0, 5)
>>> list(range(5))
[0, 1, 2, 3, 4]


>>> pow(3, 4)
81
```


Full list of functions can be [found here](https://docs.python.org/3.5/library/functions.html)

Lets try to understand `Lambda`.

Small anonymous functions can be created with the lambda keyword
```Python
def sumof(x,y):
    return x+y
```

Above function can also be represented using lambda
```python
lambda x,y: x+y
```

Lambda functions can be used wherever function objects are required. Said that, let us try some inbuilt 
functions like `map, filter`

As help help of map
```python
map(func, *iterables) --> map object
 |  
 |  Make an iterator that computes the function using arguments from
 |  each of the iterables.  Stops when the shortest iterable is exhausted.
```

we either can define a function first and then pass it as first param, or use lambda instead.
```python
map(sumof, [1,2,3], [4,5,6])
```
or 

```python
map(lambda x,y: x+y, [1,2,3], [4,5,6])
```

### File handling

Files can read/write using `open` function.

You should pass filename(string) as argument.

You can also pass mode(`'r'`, `'w'`), which is optional.

```
>>> f = open('data.txt')
>>> f
<open file 'data.txt', mode 'r' at 0x7fd3513d54b0>
>>> f = open('data.txt')
>>> for line in f:
...   print(line)
... 
If you are reading this using python,

You are on your way to become awesome python programmer.

Now that you have read the file,

try writing some text into a file.

>>>
```

Lets create and write something into a file.

```
>>> f = open('story.txt')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IOError: [Errno 2] No such file or directory: 'story.txt'
>>> f = open('story.txt', 'w')
>>> f.write('Once there lived a python programmer.')
>>> f.write('foo bar baz.')
>>> f.write('more foo')
>>> f.close()
```

### Exception handling
```python
>>> x = [5]
>>> x[2]

Traceback (most recent call last):
  File "<pyshell#120>", line 1, in <module>
    x[2]
IndexError: list index out of range
>>> x.remove(23)

Traceback (most recent call last):
  File "<pyshell#121>", line 1, in <module>
    x.remove(23)
ValueError: list.remove(x): x not in list
>>> try:
	x[4]
except:
	print 'got an exception'

	
got an exception
>>> try:
	x[4]
except IndexError:
	print 'give proper index'

	
give proper index
>>> try:
	x.remove(34)
except IndexError:
	print 'give proper index'

	

Traceback (most recent call last):
  File "<pyshell#130>", line 2, in <module>
    x.remove(34)
ValueError: list.remove(x): x not in list
>>> try:
	x.remove(34)
except IndexError:
	print 'give proper index'
except ValueError:
	print 'value not in list'

	
value not in list

>>> try:
	x.remove(34)
except IndexError:
	print 'give proper index'
except ValueError:
	print 'value not in list'
except:
	print 'go unknown exception'

	
value not in list
>>> try:
	print x[0]
	print 5/0
except IndexError:
	print 'give proper index'
except ValueError:
	print 'value not in list'
except:
	print 'got unknown exception'

	
5
got unknown exception
>>> try:
	print x[0]
	print 5/0
except Exception as ex:
	print 'got unknown exception'

	
5
got unknown exception
>>> try:
	print x[0]
	print 5/0
except Exception as ex:
	print ex

	
5
integer division or modulo by zero
>>> ex
ZeroDivisionError('integer division or modulo by zero',)
>>> ex.message
'integer division or modulo by zero'
>>> try:
	print x[0]
	print 5/0
except Exception as ex:
	print ex.message

5
integer division or modulo by zero


>>> 
>>> try:
	x[1]
except:
	print 'got exception'
finally:
	print 'inside finally'

	
got exception
inside finally
>>> try:
	x[0]
except:
	print 'got exception'
finally:
	print 'inside finally'

	
5
inside finally
```

### Classes

A class is a specification (think of it as a blueprint or pattern and a set of instructions) 
of how to provide some service. 
Engineers and construction and factory workers use blueprints to build cars, buildings, bridges, 
virtually anything.  Tailors, seamsters, printers use patterns to make the clothes we wear, 
books we read.  Chefs follow recipes to put together meals.

```python
>>> class Maths:
    def sumof(self, x, y):
        return x+y
    def mulof(self, x, y):
        return x*y

>>> obj = Maths()
>>> obj.sumof(3,4)
7
>>> obj.mulof(3,4)
12
```

Common mistakes while coding during initial days
```
>>> class Maths:
    def sumof(x, y):
        return x+y
    def mulof(x, y):
        return x*y

>>> obj = Maths()
>>> obj.sumof(3,4)
Traceback (most recent call last):
  File "<pyshell#49>", line 1, in <module>
    obj.sumof(3,4)
TypeError: sumof() takes 2 positional arguments but 3 were given
```

Below example from taken from
http://anandology.com/python-practice-book/object_oriented_programming.html#classes-and-objects
```python
class BankAccount:
    def __init__(self):
        self.balance = 0

    def withdraw(self, amount):
        self.balance -= amount
        return self.balance

    def deposit(self, amount):
        self.balance += amount
        return self.balance

>>> a = BankAccount()
>>> b = BankAccount()
>>> a.deposit(100)
100
>>> b.deposit(50)
50
>>> b.withdraw(10)
40
>>> a.withdraw(10)
90

class BankAccount:
    def __init__(self, initial_balance=0):
        self.balance = initial_balance

    def withdraw(self, amount):
        self.balance -= amount
        return self.balance

    def deposit(self, amount):
        self.balance += amount
        return self.balance
>>> obj = BankAccount(200)
>>> obj.balance
200
>>> obj.withdraw(50)
150
>>> obj.deposit(150)
300
```

Use docstring while writing code, that can be used to create documentation or while doing
help to the object

```python
>>> class BankAccount:
    """This class can be used to get the bank account details
       and also to do transaction.
    """
    def __init__(self, initial_balance=0):
        """Account holder can open their account with certail
           Initial balance, otherwise initial balace will be 0
        """
        self.balance = initial_balance

    def withdraw(self, amount):
        """This function can be used to withdraw amount from
           your account.
        """
        self.balance -= amount
        return self.balance

    def deposit(self, amount):
        """This function can be used to deposit amount into
           your account.
        """
        self.balance += amount
        return self.balance

>>> help(BankAccount)
Help on class BankAccount in module __main__:

class BankAccount(builtins.object)
 |  This class can be used to get the bank account details
 |  and also to do transaction.
 |  
 |  Methods defined here:
 |  
 |  __init__(self, initial_balance=0)
 |      Account holder can open their account with certail
 |      Initial balance, otherwise initial balace will be 0
 |  
 |  deposit(self, amount)
 |      This function can be used to deposit amount into
 |      your account.
 |  
 |  withdraw(self, amount)
 |      This function can be used to withdraw amount from
 |      your account.
```

#### Inheritance
A language feature would not be worthy of the name “class” without supporting inheritance. 
The syntax for a derived class definition looks like this:

```Python
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
```
Example
```python
>> class Alto:
    def price(self):
        return '3L INR'
    def power(self):
        return '800cc'
    def maker(self):
        return 'Maruti'

>>> obj = Alto()
>>> obj.maker()
'Maruti'
>>> obj.power()
'800cc'
>>> 
>>> 
>>> class Swift(Alto):
    def new_features(self):
        return 'airbag, bluetooth'

>>> sw_obj = Swift()
>>> sw_obj.maker()
'Maruti'
>>> sw_obj.power()
'800cc'
>>> sw_obj.new_features()
'airbag, bluetooth'
>>> 
>>> class Swift_newgen(Swift):
    def price(self):
        return '5L INR'
    def power(self):
        return '1200cc'

>>> ng_obj = Swift_newgen()
>>> ng_obj.price()
'5L INR'
>>> ng_obj.power()
'1200cc'
>>> ng_obj.maker()
'Maruti'
>>> 
```

Note: Some of the examples in this tutorial are taken form official documentation/tutorial of python3. [See here] https://docs.python.org/3/tutorial/
