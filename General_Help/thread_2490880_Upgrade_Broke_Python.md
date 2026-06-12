---
title: "Upgrade Broke Python?"
date: 2023-09-19
forum: General Help
---

### Post by bilkay on 2023-09-19
After upgrading from 18.04 to 20.04, my python2 script which previously ran fine now returns the following:

Traceback (most recent call last):
  File "/usr/local/bin/checks.py", line 10, in <module>
    import _mysql
ImportError: No module named _mysql


If I run python2 from the command line, I get the following:

Python 2.7.18 (default, Jul  1 2022, 12:27:04) 
[GCC 9.4.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import mysql
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named mysql
>>> import _mysql
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named _mysql
>>> import mysql.connector
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named mysql.connector
>>> 

Please don't tell me to upgrade to python3. My time on earth is limited. I've already wasted several hours trying to find an answer.

---

### Post by The Cog on 2023-09-19
Try this command to see what mysql packages might be available: **apt search 'python.*mysql'**

---

### Post by TheFu on 2023-09-19
> Please don't tell me to upgrade to python3. My time on earth is limited. I've already wasted several hours trying to find an answer. 
Just because you don't like the answer, that doesn't mean it isn't the required option. If you have less than a year remaining in your life, put down the computer and do something worthwhile.

Support for python2 ended around the world on 1.1.2020.  Hence, python2 isn't part of ubuntu 20.04 unless you specifically add it. Adding an unsupported program? Really?
I assume you tried to use pip to install the module?

Migrate any python you've written to python3 and if someone else wrote it, have them migrate it to python3.  If it isn't still supported, find a different solution.

---

### Post by MAFoElffen on 2023-09-19
+1 --

Convert your script to Python3. We all had to. It was no secret. We all got word on support ending for Python 2 a very long ago. It was in the IT News forever on everyone scrambling to do their conversions to prep for the End Of Life for version 2...

Just be happy that it is not Java. Things with it change and get deprecate between minor releases. That is why I stopped coding and supporting JAVA app's.

EDIT: I looked in my notes. In 2008, they announced that Python 2.7 Sunset (last release of Python2) was going to EOL in 2015. In 2014, they extended the EOL date would be extended to 2020...

---

### Post by Doug S on 2023-09-20
+1.

There is a cool program that will do the python script conversion for you "2to3" (which I only learned about last week).

```
sudo apt install 2to3
man 2to3
```

---

