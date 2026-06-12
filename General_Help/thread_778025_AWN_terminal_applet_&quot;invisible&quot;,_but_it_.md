---
title: "AWN terminal applet &quot;invisible&quot;, but it &quot;functions&quot;."
date: 2008-05-01
forum: General Help
---

### Post by SomeGuyDude on 2008-05-01
Hey all. Hardy 8.04 fresh install, installed AWN via the guide on here ([http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)).

The shutdown and logout applet has the following error in the console:

```
Traceback (most recent call last):
  File "/usr/lib/awn/applets/quit-applet/quit-applet.py", line 70, in button_press
    os.system(self.command)
AttributeError: 'App' object has no attribute 'command'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_lib_awn_applets_quit-applet_quit-applet.py.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/awn/applets/quit-applet/quit-applet.py", line 70, in button_press
    os.system(self.command)
AttributeError: 'App' object has no attribute 'comman
```d'

---

### Post by glycerine102 on 2008-05-01
My opacity was set to 0.0 by default in the AWN terminal preferences, effectively making it invisible.  Perhaps yours is the same way?

---

### Post by SomeGuyDude on 2008-05-01
> **glycerine102 said:**
> My opacity was set to 0.0 by default in the AWN terminal preferences, effectively making it invisible.  Perhaps yours is the same way?

:lolflag:

Wow. That didn't even OCCUR to me. Thanks man. Don't I feel like a horse's ***.

---

