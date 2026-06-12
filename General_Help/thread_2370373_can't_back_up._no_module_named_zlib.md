---
title: "can't back up. no module named zlib"
date: 2017-09-02
forum: General Help
---

### Post by trambar18 on 2017-09-02
i am trying to back up my files but deja up displays an error when i click on backup now saying:* backup failed,  Could not understand duplicity version*. When i type in *duplicity --version* in my terminal this is the output: 
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 30, in <module>
    import gzip
  File "/usr/local/lib/python2.7/gzip.py", line 9, in <module>
    import zlib
ImportError: No module named zlib
reinstalling duplicity or deja up doesn't work.
What should i do to be able to back up again.

---

### Post by deadflowr on 2017-09-02
Try reinstalling deja-dup and/or duplicity
```
sudo apt-get install --reinstall deja-dup
```
and/or
```
sudo apt-get install --reinstall duplicity
```

---

### Post by trambar18 on 2017-09-02
it did not work, i got the same output again

---

### Post by trambar18 on 2017-09-03
yesterday i posted a thread in wich i asked how to fix deja up and duplicity. i tried to bakcup my files but deja up gave me a message saying duplicity version not found . so i went in my terminal and typed duplicity --version . the output told me that i didn't have a python module named zlib installed so i ran these commands 
./configure --prefix=/opt/python2.7 + other options
make
make instal

i tried to backup again but i got the message saying duplicity version not found again. i retyped duplicity --version in my terminal again and i got this output: 
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 45, in <module>
    from lockfile import LockFile as FileLock
ImportError: No module named lockfile

i already tried reinstalling deja up, duplicty and python-lockfile. how can i be able to back up my files again?

---

### Post by howefield on 2017-09-03
Threads merged.

---

