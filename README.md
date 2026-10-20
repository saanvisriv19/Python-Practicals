# Python-Practicals
**STUDENT DETAILS**

| Field | Details |
|---|---|
| **Name** | Saanvi Srivastava |
| **Roll No.** | 26570051 |
| **Subject** | Object Oriented Programming using Python |
| **Semester** | I |
| **Course** | B.Sc. (Hons.) Computer Science |

## Contents

1. Quadratic equation
2. Prime numbers
3. Star pyramids
4. Character classification
5. String operations
6. Swap prefixes of two strings
7. Substring indices
8. Cubes of even integers
9. File handling
10. Dictionary of cubes
11. Tuple operations
12. Employee class and object counting
13. Class Point2D
14. Inheritance: class Point3D
15. Exception handling for a name

---
##**Practical 01 - Roots of a Quadratic Equation**

Question: Write a program to find the roots of a quadratic equation.

Input:
```python
import math

a = float(input("Enter a: "))
b = float(input("Enter b: "))
c = float(input("Enter c: "))

if a == 0:
    print("Not a quadratic equation")
else:
    d = b**2 - 4*a*c

    if d > 0:
        r1 = (-b + math.sqrt(d)) / (2*a)
        r2 = (-b - math.sqrt(d)) / (2*a)
        print("Two distinct real roots:", r1, r2)
    elif d == 0:
        print("Equal roots:", -b / (2*a))
    else:
        real = -b / (2*a)
        imag = math.sqrt(-d) / abs(2*a)
        print(f"Complex roots: {real} ± {imag}i")
```
Sample Test: a=1, b=-3, c=2 gives root 2.0 and 1.0

Output: 
<img width="1857" height="322" alt="python 1" src="https://github.com/user-attachments/assets/4f7728eb-6299-4a66-a4bc-a8b2becc05c0" />

Note:The discriminant d = b² - 4ac decides the type of roots: d > 0 gives two distinct real roots, d = 0 gives equal roots, and d < 0 gives complex roots. The check `a == 0` avoids division by zero, since the equation is not quadratic then.


---
##**Practical 02 - Prime Numbers**

Question:  Write a program to accept a number ‘n’ and  
a. Check if ’n’ is prime 
b. Generate all prime numbers till ‘n’  
c. Generate first ‘n’ prime numbers  
This program may be done using functions. 

Input:
```python
def is_prime(num):
    if num < 2:
        return False
    i = 2
    while i * i <= num:
        if num % i == 0:
            return False
        i += 1
    return True


# (a) Check whether a number is prime
num = int(input("Enter a number: "))
if is_prime(num):
    print(num, "is a prime number")
else:
    print(num, "is not a prime number")

# (b) All primes up to n
n = int(input("Enter the limit: "))
print("Prime numbers up to", n, "are:")
for i in range(2, n + 1):
    if is_prime(i):
        print(i, end=" ")
print()

# (c) First n primes
count = int(input("How many primes do you want? "))
found = 0
candidate = 2
print("First", count, "prime numbers:")
while found < count:
    if is_prime(candidate):
        print(candidate, end=" ")
        found += 1
    candidate += 1
print()
```
Sample Test: 
Enter a number: 25

25 is not a prime number

Enter the limit: 30

Prime numbers up to 30 are:

2 3 5 7 11 13 17 19 23 29

How many primes do you want? 8

First 8 prime numbers:

2 3 5 7 11 13 17 19

Output:
<img width="1847" height="317" alt="python 2" src="https://github.com/user-attachments/assets/c260c624-74ff-4001-8aa3-d2e57eb59433" />

Note: A number is prime only if it is greater than 1 and has no divisor other than 1 and itself. The loop checks divisors only up to the square root of the number, because any factor larger than that would pair with a smaller one. The same `is_prime()` function is used in all three parts.


---
##**Practical 03 - Star Pyramids**

Question: Write a program to create a pyramid of the character ‘*’ and a reverse pyramid 

Input:
```python
rows = int(input("Enter number of rows: "))

print("Pyramid:")
for i in range(1, rows + 1):
    print(" " * (rows - i) + "*" * (2 * i - 1))

print("Reverse pyramid:")
for i in range(rows, 0, -1):
    print(" " * (rows - i) + "*" * (2 * i - 1))
```

Output:
<img width="1862" height="330" alt="python 3" src="https://github.com/user-attachments/assets/f9f8bc44-7159-4c89-b89e-94750020e145" />


---
##**Practical 04 - Character Classification**

Question:  Write a program that accepts a character and performs the following:

a. print whether the character is a letter or numeric digit or a special character. 

b. if the character is a letter, print whether the letter is uppercase or lowercase 

c. if the character is a numeric digit, prints its name in text (e.g., if input is 9, output is 
NINE) 

Input: 
```python
ch = input("Enter a character: ")

if len(ch) != 1:
    print("Please enter only one character")
else:
    # a. letter, digit or special character
    if ch.isalpha():
        print("It is a letter")

        # b. uppercase or lowercase
        if ch.isupper():
            print("It is uppercase")
        else:
            print("It is lowercase")

    elif ch.isdigit():
        print("It is a numeric digit")

        # c. name of the digit
        names = ["ZERO", "ONE", "TWO", "THREE", "FOUR",
                 "FIVE", "SIX", "SEVEN", "EIGHT", "NINE"]
        print(names[int(ch)])

    else:
        print("It is a special character")
```
Sample Test: 
Enter a character: G (letter, uppercase)

Enter a character: m (letter, lowercase)

Enter a character: 4 (numeric digit, four)

Enter a character: # (special character)

Output:
<img width="1807" height="421" alt="python 4" src="https://github.com/user-attachments/assets/48d82611-ee18-47cd-b0ff-e6bfe399d2be" />


---
##**Practical 05 - String Operations**

Question:  Write a program to perform the following operations on a string 
a. Find the frequency of a character in a string. 
b. Replace a character by another character in a string. 
c. Remove the first occurrence of a character from a string. 
d. Remove all occurrences of a character from a string.

Input:
```python
s = input("Enter a string: ")
ch = input("Enter a character: ")

# a. Frequency of a character
count = 0
for c in s:
    if c == ch:
        count = count + 1
print("Frequency of", ch, "is", count)

# b. Replace a character by another character
new_ch = input("Enter the character to replace it with: ")
replaced = ""
for c in s:
    if c == ch:
        replaced = replaced + new_ch
    else:
        replaced = replaced + c
print("After replacing:", replaced)

# c. Remove the first occurrence of a character
pos = s.find(ch)
if pos == -1:
    print("Character not found")
else:
    print("After removing first occurrence:", s[:pos] + s[pos + 1:])

# d. Remove all occurrences of a character
result = ""
for c in s:
    if c != ch:
        result = result + c
print("After removing all occurrences:", result)
```

Sample Test: 
string: programming

character: m

character to replace it with: n

Output:
<img width="1852" height="317" alt="python 5" src="https://github.com/user-attachments/assets/23f0e9a0-ca42-4574-8376-4ec0487c03fd" />


---
##**Practical 06 - Swap the First n Characters of Two Strings**

Question: Write a program to swap the first n characters of two strings.

Input:
```python
s1 = input("Enter first string: ")
s2 = input("Enter second string: ")
n = int(input("Enter n: "))

new1 = s2[:n] + s1[n:]
new2 = s1[:n] + s2[n:]

print("First string after swapping:", new1)
print("Second string after swapping:", new2)
```
Sample Test: Enter first string: hello, Enter second string: world

Output:
<img width="1833" height="312" alt="image" src="https://github.com/user-attachments/assets/614b6988-dfdc-428f-9242-d425df62b40d" />


---
##**Practical 07 - Find All Indices of a Substring**

Question:  Write a function that accepts two strings and returns the indices of all the occurrences of the 
second string in the first string as a list. If the second string is not present in the first string 
then it should return -1. 

Input:
```python
def find_indices(first, second):
    indices = []
    for i in range(len(first) - len(second) + 1):
        if first[i:i + len(second)] == second:
            indices.append(i)
    if len(indices) == 0:
        return -1
    return indices


s1 = input("Enter first string: ")
s2 = input("Enter second string: ")
print(find_indices(s1, s2))
```
Sample Test: Enter first string: abababa, Enter second string: aba (found several times)

Enter first string: hello, Enter second string: xyz (a single character)

Output:
<img width="1840" height="320" alt="image" src="https://github.com/user-attachments/assets/95d7dfbe-c3a5-4ab4-9905-ed8112e8dfba" />


---
##**Practical 08 - Cubes of Even Integers in a List**

Question:  Write a program to create a list of the cubes of only the even integers appearing in the input 
list (may have elements of other types also) using the following: 
a. 'for' loop 
b. list comprehension

Input: 
```python
my_list = [1, 2, "hello", 4, 3.5, 6, 7, 8, "abc", 10]
print("Input list:", my_list)

# a. using for loop
cubes = []
for x in my_list:
    if type(x) == int and x % 2 == 0:
        cubes.append(x ** 3)
print("Using for loop:", cubes)

# b. using list comprehension
cubes2 = [x ** 3 for x in my_list if type(x) == int and x % 2 == 0]
print("Using list comprehension:", cubes2)
```

Output:
<img width="1843" height="325" alt="image" src="https://github.com/user-attachments/assets/cc51a94d-f80d-4867-9dba-5c0cb9883fd0" />


---
##**Practical 09 - File Handling**

Question: Write a program to read a file and 

a.  Print the total number of characters, words and lines in the file. 

b.  Calculate the frequency of each character in the file. Use a variable of dictionary type 
to maintain the count. 

c.  Print the words in reverse order. 

d.  Copy even lines of the file to a file named ‘File1’ and odd lines to another file named 
‘File2’. 

Input: 
```python
# Read the file
f = open("sample.txt", "r")
content = f.read()
f.close()

lines = content.splitlines()
words = content.split()

# a. Count characters, words and lines
print("Total characters:", len(content))
print("Total words:", len(words))
print("Total lines:", len(lines))

# b. Frequency of each character
freq = {}
for ch in content:
    if ch in freq:
        freq[ch] = freq[ch] + 1
    else:
        freq[ch] = 1
print("Character frequency:")
for ch in freq:
    print(ch, ":", freq[ch])

# c. Words in reverse order
print("Words in reverse order:")
for i in range(len(words) - 1, -1, -1):
    print(words[i], end=" ")
print()

# d. Even lines to File1, odd lines to File2
file1 = open("File1.txt", "w")
file2 = open("File2.txt", "w")
line_no = 1
for line in lines:
    if line_no % 2 == 0:
        file1.write(line + "\n")
    else:
        file2.write(line + "\n")
    line_no = line_no + 1
file1.close()
file2.close()
print("Done. Check File1.txt and File2.txt")
```

Sample Test: if the input file contains

Hello world

Python is fun

I love coding

File handling practical

then File1 (even lines) contains: Python is fun and File handling practical

while File2 (odd lines) contains: Hello world and I love coding

Output:
<img width="1917" height="1015" alt="python 9 1" src="https://github.com/user-attachments/assets/0b686815-3a3b-4904-a617-ce3a6debdb36" />

File1:
<img width="1473" height="932" alt="python 9 file1" src="https://github.com/user-attachments/assets/4abe138c-99f3-4bf5-be56-7827200541ab" />

File2:
<img width="1472" height="1018" alt="python 9 file2" src="https://github.com/user-attachments/assets/a1e858ef-5b9d-4c14-a22c-317d5e9bdaa1" />


---
##**Practical 10 - Dictionary of Cubes**

Question:  Write a function that prints a dictionary where the keys are numbers between 1 and 5 and the 
values are cubes of the keys. 

Input: 
```python
def print_cubes():
    cubes = {}
    for i in range(1, 6):
        cubes[i] = i ** 3
    print(cubes)


print_cubes()
```

Output:
<img width="1853" height="327" alt="python 10" src="https://github.com/user-attachments/assets/ecb245a4-0bad-41ae-945a-2f2ee57936f8" />


---
##**Practical 11 - Tuple Operations**

Question: Consider a tuple t1=(1, 2, 5, 7, 9, 2, 4, 6, 8, 10). Write a program to perform following 
operations: 

a. Print half the values of the tuple in one line and the other half in the next line. 

b. Print another tuple whose values are even numbers in the given tuple. 

c. Concatenate a tuple t2=(11,13,15) with t1. 

d. Return maximum and minimum value from this tuple 

Input:
```python
t1 = (1, 2, 5, 7, 9, 2, 4, 6, 8, 10)
t2 = (11, 13, 15)

# a. Print half the values in one line and the other half in the next line
half = len(t1) // 2

for i in range(half):
    print(t1[i], end=" ")
print()

for i in range(half, len(t1)):
    print(t1[i], end=" ")
print()

# b. Print another tuple whose values are the even numbers
even = ()
for x in t1:
    if x % 2 == 0:
        even = even + (x,)
print("Tuple of even numbers:", even)

# c. Concatenate t2 with t1
t3 = t1 + t2
print("Concatenated tuple:", t3)


# d. Return maximum and minimum value from the tuple
def max_min(t):
    return max(t), min(t)


largest, smallest = max_min(t1)
print("Maximum value:", largest)
print("Minimum value:", smallest)
```

Output:
<img width="1843" height="325" alt="image" src="https://github.com/user-attachments/assets/ff99dfca-e419-4271-8e33-12b3e1d8b5e0" />


---
##**Practical 12 - Employee Class and Object Counting**

Question:  Define a class Employee that stores information about employees in the company. The class 
should contain the following: 

(i)   data members- count (to keep a record of all the objects being created for this class) 
and for every employee: an employee number, Name, Dept, Basic, DA and HRA.   

(ii)  function members: 

a.  __init__ method to initialize and/or update the members. Add statements to ensure 
that the program is terminated if any of Basic, DA and HRA is set to a negative 
value. 

b.  function salary, that returns salary as the sum of Basic, DA and HRA. 

c.  __del__ function to decrease the number of objects created for the class. 

d.  __str __ function to display the details of an employee along with the salary of an 
employee in a proper format. 

Input: 
```python
import sys


class Employee:
    count = 0                       # class variable: shared by all employees

    def __init__(self, emp_no, name, dept, basic, da, hra):
        if basic < 0 or da < 0 or hra < 0:
            print("Basic, DA and HRA cannot be negative. Program terminated.")
            sys.exit()

        self.emp_no = emp_no
        self.name = name
        self.dept = dept
        self.basic = basic
        self.da = da
        self.hra = hra
        Employee.count = Employee.count + 1

    def salary(self):
        return self.basic + self.da + self.hra

    def __del__(self):
        Employee.count = Employee.count - 1

    def __str__(self):
        return ("Employee Number : " + str(self.emp_no) + "\n" +
                "Name            : " + self.name + "\n" +
                "Department      : " + self.dept + "\n" +
                "Basic           : " + str(self.basic) + "\n" +
                "DA              : " + str(self.da) + "\n" +
                "HRA             : " + str(self.hra) + "\n" +
                "Salary          : " + str(self.salary()))


e1 = Employee(101, "Amit", "Sales", 30000, 15000, 9000)
e2 = Employee(102, "Neha", "HR", 40000, 20000, 12000)

print(e1)
print()
print(e2)
print()
print("Total employees:", Employee.count)

del e2
print("After deleting e2, total employees:", Employee.count)
```

Output:
<img width="1811" height="626" alt="image" src="https://github.com/user-attachments/assets/75b5374f-14b8-49ff-86ed-d99fd911ebe3" />

Testing the negative value check:

Adding this at the end of the above input,

e3 = Employee(103, "Ravi", "IT", -5000, 10000, 5000)

Output:
<img width="1582" height="481" alt="image" src="https://github.com/user-attachments/assets/020eb987-5031-4354-8721-12a20af3eb34" />


---
##**Practical 13 - Class Point2D**

Question: . Write a program to define a class "2DPoint" with coordinates x and y as attributes. Create 
relevant methods and print the objects. Also define a method distance to calculate the 
distance between any two point objects.

Input:
```python
import math


class Point2D:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __str__(self):
        return "(" + str(self.x) + ", " + str(self.y) + ")"

    def distance(self, other):
        dx = self.x - other.x
        dy = self.y - other.y
        return math.sqrt(dx ** 2 + dy ** 2)


p1 = Point2D(1, 2)
p2 = Point2D(4, 6)
p3 = Point2D()

print("Point 1:", p1)
print("Point 2:", p2)
print("Point 3 (default):", p3)
print("Distance between p1 and p2:", p1.distance(p2))
print("Distance between p1 and p3:", p1.distance(p3))
```

Output:
<img width="1836" height="327" alt="image" src="https://github.com/user-attachments/assets/83c5285c-bdef-4bc5-84a1-8ae3d5e7fec6" />


---
##**Practical 14 - Inheritance: Class Point3D**

Question: Inherit the above class to create a "3Dpoint" with additional attribute z. Override the method 
defined in "2DPoint" class , to calculate distance between two points of the "3DPoint" class.

Input: 
```python
import math


class Point2D:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __str__(self):
        return "(" + str(self.x) + ", " + str(self.y) + ")"

    def distance(self, other):
        dx = self.x - other.x
        dy = self.y - other.y
        return math.sqrt(dx ** 2 + dy ** 2)


class Point3D(Point2D):
    def __init__(self, x=0, y=0, z=0):
        super().__init__(x, y)
        self.z = z

    def __str__(self):
        return "(" + str(self.x) + ", " + str(self.y) + ", " + str(self.z) + ")"

    def distance(self, other):
        dx = self.x - other.x
        dy = self.y - other.y
        dz = self.z - other.z
        return math.sqrt(dx ** 2 + dy ** 2 + dz ** 2)


# 2D points (parent class)
a = Point2D(1, 2)
b = Point2D(4, 6)
print("2D point a:", a)
print("2D point b:", b)
print("2D distance:", a.distance(b))

print()

# 3D points (child class)
p1 = Point3D(1, 2, 3)
p2 = Point3D(4, 6, 15)
p3 = Point3D()
print("3D point p1:", p1)
print("3D point p2:", p2)
print("3D point p3 (default):", p3)
print("3D distance between p1 and p2:", p1.distance(p2))
print("3D distance between p1 and p3:", p1.distance(p3))
```

Output:
<img width="1841" height="312" alt="image" src="https://github.com/user-attachments/assets/9fa557fe-d85c-4aca-977b-95b41ae2eac8" />


---
##**Practical 15 - Exception Handling for a Name**

Question: . Write a program to accept a name from a user. Raise and handle appropriate exception(s) if 
the text entered by the user contains digits and/or special characters.

Input: 
```python
def check_name(name):
    if name.strip() == "":
        raise ValueError("Name cannot be empty")

    has_digit = False
    has_special = False

    for ch in name:
        if ch.isdigit():
            has_digit = True
        elif not ch.isalpha() and ch != " ":
            has_special = True

    if has_digit and has_special:
        raise ValueError("Name contains digits and special characters")
    elif has_digit:
        raise ValueError("Name contains digits")
    elif has_special:
        raise ValueError("Name contains special characters")


try:
    name = input("Enter your name: ")
    check_name(name)
    print("Valid name. Hello,", name)
except ValueError as e:
    print("Invalid name:", e)
```

Sample Test:
Enter your name: Saanvi Srivastava

Valid name. Hello, Saanvi Srivastava

Enter your name: Saanvi123

Invalid name: Name contains digits

Enter your name: Saanvi@#

Invalid name: Name contains special characters

Enter your name: Saanvi12@#

Invalid name: Name contains digits and special characters

Enter your name:

Invalid name: Name cannot be empty

Output:
<img width="1832" height="530" alt="image" src="https://github.com/user-attachments/assets/10c38f6c-7b53-4b18-90ef-5c283792ca1d" />

---



















