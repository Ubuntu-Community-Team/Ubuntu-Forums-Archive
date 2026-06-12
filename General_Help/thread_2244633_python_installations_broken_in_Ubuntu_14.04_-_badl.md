---
title: "python installations broken in Ubuntu 14.04 - badly configured"
date: 2014-09-17
forum: General Help
---

### Post by rwohlhueter on 2014-09-17
I have installed both python 2.7 and 3.4 on my AMD64-bit Ubuntu 14.04 system.  I don't use Python directly, but several applications I use are at least partially implemented in python.  Both 2.7 and 3.4 were installed via Synaptic (apparently without problems), but neither installation works.
For example, if I simply issue the `python` command (which in /usr/bin is linked to python2.7), I get:

bobw@winter: [416]> python
python
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 578, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 524, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 408, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd


That is, the (unaltered)  site.py installed with python2.7 seems to contain syntax errors.  I would guess that python is not properly configured for my machine, But the man-age for "python-config is truly daunting, and I I expect I could do lots of damage fiddling with it.

Is there no more-or-less easy, automated way to configure python:

Thanks, Bob Wohlhueter

---

### Post by ian-weisser on 2014-09-17
I'm confused....

Python 2.7 and Python 3.4 are already included out-of-the box with every flavor of Ubuntu 14.04.
You shouldn't need to install them.
Trying to install/reinstall over the existing versions should be a quite difficult feat to accomplish in Synaptic.

Exactly which packages did you install?

---

### Post by rwohlhueter on 2014-09-18
That's my point:  both versions (2.7 and 3.4 are installed; I haven't fiddled with the installations at all (and am loath to do so).  Still the "out-of'-the'box" 2.7 gives the the errors I list in my original note.

---

