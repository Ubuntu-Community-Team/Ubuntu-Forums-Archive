---
title: "deskbar applet bug report"
date: 2007-12-20
forum: General Help
---

### Post by ares623 on 2007-12-20
this keeps on popping  up everytime i log-in. i already reported it. don't know what's causing it.. it still functions fine afaik
[[IMG]http://img511.imageshack.us/img511/2456/screenshotfw7.th.png[/IMG]](http://img511.imageshack.us/my.php?image=screenshotfw7.png)
EDIT: here is the detailed error report
```
Distribution: Ubuntu 7.10 (gutsy)
Gnome Release: 2.20.1 2007-10-19 (Ubuntu)
BugBuddy Version: 2.18.1

System: Linux 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10300000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Human
Icon Theme: Human

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0



----------- .xsession-errors ---------------------
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]: 	       Name: Local Directory Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control active.
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'
--------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/deskbar/core/CoreImpl.py", line 314, in on_module_initialized
    self._history.load()
  File "/usr/lib/python2.5/site-packages/deskbar/core/DeskbarHistory.py", line 113, in load
    saved_history = cPickle.load(file(HISTORY_FILE))
EOFError

```

---

### Post by RacerII on 2007-12-28
I had the same problem , but only when i used dual x displays.
I just uninstalled deskbar to get rid of the error ... and deskbar.

---

