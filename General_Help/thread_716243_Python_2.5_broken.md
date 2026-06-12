---
title: "Python 2.5 broken"
date: 2008-03-05
forum: General Help
---

### Post by furk on 2008-03-05
Hi all there! :) This is my first post here...i hope this is the right section for my problem :confused:

My python 2.5 installation seems corrupted after an unclean shutdown.

This is what i get:
```

>>> import mimetools
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/mimetools.py", line 11, in <module>
    class Message(rfc822.Message):
AttributeError: 'module' object has no attribute 'Message'
>>> 
```

How may i fix it? :confused::confused::confused:

---

### Post by Juffo-Wup on 2008-03-05
Have you tried reinstalling it from Synaptic (or Adept, if you're using Kubuntu)?

---

### Post by furk on 2008-03-06
Fixed.  :D 

All was due to the unclean shutdown that caused some troubles and inconsistency in file system. 

Forcing an fsck solved all.

Thank's mate.

---

