---
title: "Python Import error"
date: 2016-10-20
forum: General Help
---

### Post by fauzan2 on 2016-10-20
I installed pydrive using pip. I tried to test a python script which uses PyDrive, but got the error
```
ImportError: No module named 'PyDrive'
```

The I tried ```
pip show pydrive

Traceback (most recent call last):
  File "quick.py", line 1, in <module>
    from PyDrive.drive import GoogleAuth
ImportError: No module named 'PyDrive'

```

In fact, pip list shows a lot of installed packages, but most of them a re showing import errors. How to fix this issue?

---

### Post by Zero_Bytes on 2016-10-20
Have you tried making a virtual environment and installing it in there?

[http://docs.python-guide.org/en/latest/dev/virtualenvs/](http://docs.python-guide.org/en/latest/dev/virtualenvs/)

---

### Post by fauzan2 on 2016-10-20
OK, so the import was working in python, not in python3. So I installed pip3 and then installed pydrive using pip3. However, there some other errors now, not relevant to this question.

---

