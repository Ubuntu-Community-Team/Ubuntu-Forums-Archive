---
title: "update-manager invalid syntax"
date: 2006-10-28
forum: General Help
---

### Post by jok on 2006-10-28
hi, i just installed edgy. most of it seems to work. however, starting update-manager gives me a syntax error. any idea? thanks .

```
$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in ?
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 59, in ?
    import dbus
  File "/var/lib/python-support/python2.4/dbus/__init__.py", line 1, in ?
    from _dbus import *
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 46, in ?
    import weakref
  File "/usr/lib/python2.4/weakref.py", line 247
    !wr = ref(key)
    ^
SyntaxError: invalid syntax
```

---

### Post by jok on 2006-10-28
ich removed the "!" in File "/usr/lib/python2.4/weakref.py", line 247. Now it works. I wonder how this could happen. o.O

---

