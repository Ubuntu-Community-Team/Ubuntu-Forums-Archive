---
title: "Fatal Python error -- can not do apt-get update anymore"
date: 2013-01-01
forum: General Help
---

### Post by rudolfl on 2013-01-01
Hi, all

Tried to upgrade from 12.04 to 12.10 and had power failure in the process.

Now, apt-get update doe snot work anymore, as there is a problem with one of the basic packages -- python3.2-minimal

Trying to re-configure it and I am getting:
Fatal Python error: Py_initialize: Unable to get locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)

This error happens in postinst script of the package.

Tried to run 'python' and it runs OK and it is python 2.7/
Running python3 generates error above.

In fact, this error is generated if run anything that is not a command. For example, "crap" is not a command or program and running it generates same error. So, system is badly broken.

Any ideas on how to fix it? I am afraid on removing the python3 completely and I believe it will make things worse

Rudolf

---

### Post by Calinou on 2013-01-01
Try reinstalling it with:
sudo apt-get install --reinstall python3

(Python 3 is the default since 12.04)

---

### Post by rudolfl on 2013-01-01
Thanks,

I tried that before and it did not work.
E: Internal error, No file name for python3:i386

In the meantime I progressed a bit further.
Went into /car/cache/apt/archives
and installed (with dpkg -i) python3.2-minimal and python3 DEB packages.
OK, now python3 works, but apt-get update fails anyway. Fails to configure python3-minimal (python3.2-minimal is already installed, but problem is with python3-minimal)
Error is:
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 34 in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
EOFError: EOF read where not expected

Will keep digging.

Rudolf

---

### Post by rudolfl on 2013-01-01
OK, I think, this one is fixed as well. 

rm /usr/share/python3/debpython/__pycache__/*

This will get rid of old compiled Python files (I guess, some of them were corrupted due to previous problems).

Now, I could install python3-minimal and python3 as well and apt-get upgrade works.

Rudolf

---

