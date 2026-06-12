---
title: "kcontrol broke"
date: 2007-12-23
forum: General Help
---

### Post by phatbastard on 2007-12-23
spaceballs:~$ kcontrol
phatbastard@spaceballs:~$

Pythonize constructor -- pid = 7744
Python interpreter initialized!



Pythonize constructor -- pid = 7744
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_serviceconfig
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 1455, in create_serviceconfig
    return SysVInitApp(parent, name)
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 958, in __init__
    self.context.loadInfo()
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 303, in loadInfo
    rl.loadInfo()
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 323, in loadInfo
    for filename in os.listdir(self.leveldir):
OSError: [Errno 2] No such file or directory: '/etc/rc.d/rc0.d'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_serviceconfig
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 1455, in create_serviceconfig
    return SysVInitApp(parent, name)
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 958, in __init__
    self.context.loadInfo()
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 303, in loadInfo
    rl.loadInfo()
  File "/var/lib/python-support/python2.5/serviceconfig.py", line 323, in loadInfo
    for filename in os.listdir(self.leveldir):
OSError: [Errno 2] No such file or directory: '/etc/rc.d/rc0.d'
error: *** runFunction failure


I can view everything in kcontrol, but i cant view System Administration > System Services. I am using kubuntu.

---

### Post by phatbastard on 2007-12-23
bump

---

