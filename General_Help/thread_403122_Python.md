---
title: "Python"
date: 2007-04-06
forum: General Help
---

### Post by ali780 on 2007-04-06
Hello
How can I install Python on my Ubuntu ?
Thanks

---

### Post by maxamillion on 2007-04-06
Python is installed on Ubuntu by default.

If you need any python extras you can check synaptic, aptitude, or apt-get to see what all is available in the repositories and install what you need or want.

---

### Post by ali780 on 2007-04-06
thanks for fast reply
Yes it is installed but I guess something is wrong. Because when I want write a multi line command it reports an error. See blow for example:
>>> a,b=0,1
>>> while b <1000:
... print b,
  File "<stdin>", line 2
    print b,
        ^
IndentationError: expected an indented block
>>> 
may I have written wrong.

---

### Post by WW on 2007-04-06
In python, you *must* indent the statements in the while loop:
```

~$ python
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> b = 1
>>> while b < 5:
...     print b
...     b = b + 1
...
1
2
3
4
>>>

```
After the last statement in the while loop, hit enter at the ... prompt.  The while loop will then execute.

---

### Post by ali780 on 2007-04-06
thank you very much

---

