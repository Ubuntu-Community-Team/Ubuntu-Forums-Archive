---
title: "Help with Maths in bash."
date: 2017-08-15
forum: General Help
---

### Post by CaptainMark on 2017-08-15
Can someone help me out a little with some maths. I've no idea how to do maths in bash as I've never had to other than incrementing numbers by 1. I've got a PC at work that I'd like to set up a simple script that needs to:

1. Ask the user for a number to two decimal places.

2. Get the reciprocal of the number (1/number)

3. Subtract 0.01 from the newer number

4. Get the reciprocal of this newest number and round it off to the nearest 0.25

I haven't a clue how to do any of these things in bash. The pc also has python 2.4 installed which I can use, but I can't add additional software to this machine at all. 

Thanks for any tips 

Regards
Mark.

---

### Post by SeijiSensei on 2017-08-15
Look at the expr command in bash.  For instance
```
$ expr 1 + 2 
3

```
Spacing matters here because bash uses the space as a delimiter.  
```

expr 1+2 
1+2

```
Without spaces around the plus sign, expr treats the argument as a string.

Algebraic:
```

$ A=1
$ B=2
$ expr $A + $B
3

```

Rounding might be a bit tricky since expr doesn't like floating-point numbers.  Here are some tips for that:  [https://stackoverflow.com/questions/1253987/how-to-use-expr-on-float](https://stackoverflow.com/questions/1253987/how-to-use-expr-on-float)

---

### Post by CaptainMark on 2017-08-15
Unfortunately this won't cut it then, floating point numbers are essential to this, I need the calculation reciprocals done to at least 5 decimal places. Would I be better using python?

---

### Post by vocx on 2017-08-15
> **CaptainMark said:**
> Unfortunately this won't cut it then, floating point numbers are essential to this, I need the calculation reciprocals done to at least 5 decimal places. **Would I be better using python?**
Python is a general purpose programming language used by millions of engineers and scientists in the world to do complex numerical calculations in the fields of electrical, mechanical, aerospace, chemical engineering, data science, computer science, robotics, machine vision, machine learning, financial statistics, et cetera. So, yes, Python is much more suited for handling numbers with unlimited precision.

I won't teach you to use Python in this thread simply because it would be rehashing the information you can easily find somewhere else. There are many guides that explain how to use Python as a calculator. It's really simple, actually. You just use the use the normal operators / + - * to perform the operations and get the result. You would usually save the result to a variable, and then you can print it with the precision you need.
```

a = 1
b = 2.0
c = a + b
print('%5.5f' % c)

```

```

# for old python versions, the print statement doesn't use parentheses

print '%5.5f' % c

```

Edit. Oh, you have access to Python 2.4? That is bad. Python 2.4 is basically obsolete. The minimum version that you should be using is 2.7. Newer versions, in the Python 3 series, are also fine but the bare minimum should be 2.7.

To do very simple numerical calculations like / + - *, any Python version is fine but you should avoid developing big programs in versions older than 2.7, unless you know which features are compatible with the more recent versions.

Although you say you cannot install new software, it may be possible to get a minimalistic Python 2.7 that is self contained and runs inside a folder and thus does not need "installing". You may look for this option.

---

### Post by yancek on 2017-08-15
I don't think you can do decimals in straight bash but need to pipe to bc.  You might google using bc with bash.  I'm posting a simple script I found online which uses bc.  Modify it to suit your needs.

```
#!/bin/bash
#this is program which takes 2 numbers as input and multiplies them
while [ "$ps" != 0 ]
do
read -p "ps:" ps
read -p "num:" num
printf "Result: "
echo "$ps * $num" | bc
done
exit 0
```

---

