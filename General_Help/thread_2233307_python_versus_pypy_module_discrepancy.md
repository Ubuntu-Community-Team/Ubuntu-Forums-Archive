---
title: "python versus pypy: module discrepancy?"
date: 2014-07-07
forum: General Help
---

### Post by sanderj on 2014-07-07
Hi,

I have mini python script hallo.py:

```
import Cheetah
print "Hello there!"
```

It works with python, but not with pypy:

```
$ python hallo.py 
Hello there!
```

```
$ pypy hallo.py 
Traceback (most recent call last):
  File "app_main.py", line 72, in run_toplevel
  File "hallo.py", line 1, in <module>
    import Cheetah
ImportError: No module named Cheetah
```

Tips how to solve this?

FWIW:

[https://bitbucket.org/pypy/compatibility/wiki/Home](https://bitbucket.org/pypy/compatibility/wiki/Home) says Cheetah is compatible.


```
$ pypy
Python 2.7.3 (2.2.1+dfsg-1, Nov 28 2013, 05:13:10)
[PyPy 2.2.1 with GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
And now for something completely different: ``I've got this floor wax that's
also a GREAT dessert topping!!''
>>>> 
```


[ Ubuntu 14.04 64-bit ]

---

### Post by sanderj on 2014-07-07
Thanks to [http://stackoverflow.com/questions/11195273/getting-pypy-to-recognize-third-party-modules/11195467#11195467](http://stackoverflow.com/questions/11195273/getting-pypy-to-recognize-third-party-modules/11195467#11195467), this seems to work:

```
import sys
sys.path.insert(0, '/usr/lib/python2.7/dist-packages/')

import Cheetah
print dir(Cheetah)

print "Hello there!"
```

```
$ python hallo.py 
['MinCompatibleVersion', 'MinCompatibleVersionTuple', 'Version', 'VersionTuple', '__builtins__', '__doc__', '__file__', '__name__', '__package__', '__path__', 'convertVersionStringToTuple']
Hello there!
```


```
$ pypy hallo.py 
['MinCompatibleVersion', 'MinCompatibleVersionTuple', 'Version', 'VersionTuple', '__builtins__', '__cached__', '__doc__', '__file__', '__name__', '__package__', '__path__', 'convertVersionStringToTuple']
Hello there!
```

---

