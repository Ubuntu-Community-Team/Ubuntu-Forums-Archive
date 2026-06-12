---
title: "Python error"
date: 2013-11-18
forum: General Help
---

### Post by somethingforyou on 2013-11-18
Hi,

Since installing a third party package, I get the follwing errors when I try to start Pidgin:

```
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 562, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 544, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 271, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 246, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 236, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 577, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 476, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 355, in _init_posix
    raise IOError(msg)
IOError: invalid Python installation: unable to open /usr/include/python2.7/pyconfig.h (Permission denied)


```

I searched for solutions but the ones I found didnt work (change permissions of pyconfig.h and download python and reinstall).


Hope someone here can help me get this fixed as Im pretty new :)


mahdi

---

### Post by somethingforyou on 2013-11-18
Its ok, I found the problem. It was apparmor.

---

