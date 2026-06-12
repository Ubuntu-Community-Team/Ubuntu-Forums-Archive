---
title: "Ubuntu 20.04: Python 'ModuleNotFoundError: No module named 'apt_pkg'?"
date: 2020-05-21
forum: General Help
---

### Post by afrodeity on 2020-05-21
Managed to break my python installation.

```
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 28, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 19, in <module>
    from CommandNotFound.db.db import SqliteDatabase
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/db.py", line 5, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
```

There are a few similar examples, [here]("https://stackoverflow.com/questions/56218562/how-to-fix-modulenotfounderror-no-module-named-apt-pkg") and [here]("https://askubuntu.com/questions/1069087/modulenotfounderror-no-module-named-apt-pkg-error?noredirect=1&lq=1")

```
update-alternatives --config python3

There are 2 choices for the alternative python3 (providing /usr/bin/python3).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python3.7   2         auto mode
  1            /usr/bin/python3.6   1         manual mode
  2            /usr/bin/python3.7   2         manual mode
```

setting to auto or choosing either doesn't help

editing /usr/bin/add-apt-repository doesnt help:

```
 nano /usr/bin/add-apt-repository   
                      
#!/usr/bin/python3.7
```

if I do this: 
```
ls -l /usr/lib/python3/dist-packages/apt_pkg*
-rw-r--r-- 1 root root 359376 Apr  9 09:16 /usr/lib/python3/dist-packages/apt_pkg.cpython-38-x86_64-linux-gnu.so

/usr/lib/python3/dist-packages/apt_pkg-stubs:
total 12
-rw-r--r-- 1 root root 11139 Apr  9 09:16 __init__.pyi

```

Which is a bit weird since it seems that python 3.8 is installed.

At a loss right now, and eyes wont let me continue.

---

### Post by afrodeity on 2020-05-21
okay, some rest and another look

this fixed it

```
sudo ln -s apt_pkg.cpython-38-x86_64-linux-gnu.so apt_pkg.so
```

---

