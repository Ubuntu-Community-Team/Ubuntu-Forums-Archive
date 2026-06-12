---
title: "Use alias names in command"
date: 2013-04-11
forum: General Help
---

### Post by elang on 2013-04-11
I want to use alias names as inputs so as to save time. Is there a way to define aliases in such a way so as to achieve that?

_**E.g.**_ if have a lot of python scripts in my /home/pycodes/ folder name as TestCaseXXX where XXX denotes a three digit number.
      Can I define an alias (say like pyrun), that when i type **pyrunXXX** , the resulting command = **python /home/pycodes/Testcasexxx.py** ??

---

### Post by matt_symes on 2013-04-11
Hi

I would be tempted to use a function for this type of thing.

Take a look at this.
```

matthew-S206:/home/matthew % ls -l tmp[1-3]
-rwxr-xr-x 1 matthew matthew 13 Apr 11 20:22 tmp1*
-rwxr-xr-x 1 matthew matthew 13 Apr 11 20:22 tmp2*
-rwxr-xr-x 1 matthew matthew 13 Apr 11 20:22 tmp3*
matthew-S206:/home/matthew % 
```
```

matthew-S206:/home/matthew % cat tmp[1-3]
echo In tmp1
echo In tmp2
echo In tmp3
matthew-S206:/home/matthew %
```

```
matthew-S206:/home/matthew % function c { /home/matthew/tmp${1} }
matthew-S206:/home/matthew % 
```

```
matthew-S206:/home/matthew % c 1
In tmp1
matthew-S206:/home/matthew % c 2
In tmp2
matthew-S206:/home/matthew % c 3
In tmp3
matthew-S206:/home/matthew % c 4
c: no such file or directory: /home/matthew/tmp4
matthew-S206:/home/matthew % 
```

It's not an alias and requires a space between the function name and parameter but it is far more extendible than an alias.

Kind regards

---

### Post by elang on 2013-04-24
That sounds great. Can you tell me how to use a function (of which I know next to nothing about) to achieve my goal (like running the python codes above)?

---

### Post by Vaphell on 2013-04-24
something like
```
pyrun() { python /home/pycodes/Testcase${1}.py; }
```

you can also create a script and put it in $HOME/bin

```
#!/bin/bash
python /home/pycodes/Testcase${1}.py
```

in both cases *pyrun 123* will put 123 in place of $1

---

