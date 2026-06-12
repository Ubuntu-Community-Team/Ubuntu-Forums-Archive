---
title: "Screenlets Lock Up"
date: 2008-05-29
forum: General Help
---

### Post by mescaleeto on 2008-05-29
Hi, I'm new to these screenlets and I've noticed a few quirks. First certain screenlets open multiple instances, which becomes a little irritating. Second when I right click on on the screenlets they lock up to where I can't move or right click on them. I'm running compiz and awn, if that makes any difference. 

Thanks in advance.

---

### Post by hal8000 on 2008-05-29
> **mescaleeto said:**
> Hi, I'm new to these screenlets and I've noticed a few quirks. First certain screenlets open multiple instances, which becomes a little irritating. Second when I right click on on the screenlets they lock up to where I can't move or right click on them. I'm running compiz and awn, if that makes any difference. 

Thanks in advance.

Its possible avant window manager may be the cause. Im running compiz fusion and screenlets on Hardy without problem, just installed awn-manager and started it at a terminal and it crashes:-

anc@orac:~$ awn-manager 
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_awn-manager.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue


restarting awn still had same crash.

How are you invoking awn ?

---

