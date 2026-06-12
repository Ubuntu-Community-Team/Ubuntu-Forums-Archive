---
title: "Python3: TypeError: unsupported operand type(s) for %: 'NoneType' and 'str'"
date: 2014-01-02
forum: General Help
---

### Post by SWGraphics291 on 2014-01-02
Using Python3 I am trying to make a easy-to-use dart scoring program. But I came across a problem I cant find out how to fix.
Here is my script:
```
single = input ("Single's: ")
startdouble = input ("Double's: ")
starttriple = input ("Triple's: ")
startnumber = input ("What number are you starting at?: ")

double = startdouble * 2
triple = starttriple * 3

total = single + double + triple

print ("Your score: %d ") % total

currentnumber = (startnumber) - (single + double + triple)

print ("You are now on: %d ") % current


```

---

### Post by SWGraphics291 on 2014-01-02
Here is the problem:
```
Your score: %d 
Traceback (most recent call last):
  File "/home/aaron/Documents/Dart_Scorer.py", line 11, in <module>
    print ("Your score: %d ") % total
TypeError: unsupported operand type(s) for %: 'NoneType' and 'str'

```

---

