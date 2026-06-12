---
title: "Deluge won't start"
date: 2008-05-10
forum: General Help
---

### Post by tabithaboof on 2008-05-10
I have an error when I try to start Deluge, I am guessing its something to do with Python but I am not sure, I have tried to uninstall and reinstal a few times but no luck so far. Any ideas?

```

Traceback (most recent call last):
  File "/usr/bin/deluge", line 123, in <module>
    subprocess.Popen(["dbus-launch", "deluge"] + sys.argv[1:])
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_deluge.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/deluge", line 123, in <module>
    subprocess.Popen(["dbus-launch", "deluge"] + sys.argv[1:])
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
david@david-laptop:~$

```

---

