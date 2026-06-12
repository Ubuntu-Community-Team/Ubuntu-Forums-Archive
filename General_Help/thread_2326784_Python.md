---
title: "Python"
date: 2016-06-04
forum: General Help
---

### Post by Allisterguy on 2016-06-04
hi

I have two questions
1.
I am trying to learn Python! and am using  "Python The Ultimate beginners guide: start coding today.
In chapter two 
I have to type in terminal:-
D = ,686

For p in range (50,150): print p, p *d

I should get a two column list of numbers But I get:- 
 
File "<stdin>", line 1
    For p in range (50,150): print p, p*d
        ^
SyntaxError: invalid syntax

2.
I am unclear what Idle is, is it part of python. The python version I am using is 3.5 And Ubuntu is 16 04
help greatly appreciated
ACG

---

### Post by steeldriver on 2016-06-04
Be careful with letter case: **D** is not the same as **d** and **F**or is not the same as **f**or

Also remember that in python, indentation of your code is not just to make it look pretty: you must 'tab' in the body of the for loop:

```

>>> d = 1.686
>>> for p in range (50,150):
...     print p, p *d
... 

```

---

### Post by Allisterguy on 2016-06-04
Hi Thanks for the reply
I am typing exactly as in the book and the same case as the book.

D = 1,686
For p in range (50,150): print p, p*d

And I should get:-
95 160.17
96 160 856
97 163 542
98 165 228
99 166 914
100 168.6
and so on till 105 177.03

I have typed in a low case d but still got the same error message.

just don't understand it
ACG

---

### Post by steeldriver on 2016-06-04
I'm not familiar with that book, I can only tell you what should work based on experience

Also, it looks like python2 code so make sure you are using the python2 interpreter not the python3 (or 3.5) interpreter - for example, the print statement has been replaced by a function requiring parentheses in python3, i.e.

```

>>> d = 1.686
>>> for p in range (50,150):
...     print **(**p, p*d**)**

```

---

