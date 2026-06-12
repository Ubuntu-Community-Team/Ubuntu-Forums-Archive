---
title: "Switching Python Version in 18.04"
date: 2020-03-09
forum: General Help
---

### Post by weehongaiden on 2020-03-09
Hi everyone,

Ubuntu installed Python in the system and the terminal is using 2.6 by default.
Can I replace the python command version from 2.6 to version 3.8(download from apt) instead of 3.6(built-in)?

Would this cause any issue to the Ubuntu OS?

---

### Post by TheFu on 2020-03-09
Don't do that.  The OS expects the OS version of python, ruby, perl to be untouched.

You can use **pyenv** to load a different python version and use it as needed, when needed, however. There are other tools and methods similar to pyenv too.
```
$ pyenv shims
/home/tf/.pyenv/shims/idle
/home/tf/.pyenv/shims/idle3
/home/tf/.pyenv/shims/idle3.6
/home/tf/.pyenv/shims/pip
/home/tf/.pyenv/shims/pip3
/home/tf/.pyenv/shims/pip3.6
/home/tf/.pyenv/shims/python
/home/tf/.pyenv/shims/python3
/home/tf/.pyenv/shims/python3.6
/home/tf/.pyenv/shims/python3.6m
/home/tf/.pyenv/shims/python-config
/home/tf/.pyenv/shims/pyvenv
/home/tf/.pyenv/shims/pyvenv-3.6

$ which python
/home/tf/.pyenv/shims/python
$ python --version
Python 2.7.12
$ which python3
/home/tf/.pyenv/shims/python3
R$ python3 --version
Python 3.5.2
```

Seems like your system is out of date. Have you patched the OS in a year?  I'm running 16.04 and have
```
$ /usr/bin/python --version
Python 2.7.12
```
Seems that 18.04 would have at least that version.

---

### Post by CelticWarrior on 2020-03-09
```
Python 2.7.17 + Python 3.7.5
```
in a fully updated Ubuntu 19.10.

---

### Post by coffeecat on 2020-03-09
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by mörgæs on 2020-03-09
> **CelticWarrior said:**
> ```
Python 2.7.17 + Python 3.7.5
```
in a fully updated Ubuntu 19.10.

+1
Much easier to select a suitable Ubuntu version than trying to modify 18.04.

---

