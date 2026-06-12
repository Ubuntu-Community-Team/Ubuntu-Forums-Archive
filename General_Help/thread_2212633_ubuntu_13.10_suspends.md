---
title: "ubuntu 13.10 suspends"
date: 2014-03-22
forum: General Help
---

### Post by ginar2 on 2014-03-22
Hi;
My system is combined KDE+ubuntu 13.10. Very often - sometimes several times per day system stops working without any sign. Even  keybord and mouse don't respond. 
When system is restarted I can see error message:
[http://zapodaj.net/93a621d986d9f.png.html](http://zapodaj.net/93a621d986d9f.png.html)

/var/crash contains: _usr_bin_Xorg.0.crash
somthing like this:
```
ProblemType: Crash
Architecture: amd64
CrashCounter: 1
Date: Fri Mar 14 20:03:18 2014
DistroRelease: Ubuntu 13.10
ExecutablePath: /usr/bin/Xorg
ExecutableTimestamp: 1387274935
ProcCmdline: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
ProcCwd: /etc/X11
ProcEnviron: 
ProcMaps:
 7f822cdd9000-7f822d469000 rw-s 00000000 00:04 5144646                    /SYSV00000000 (deleted)
 7f822db24000-7f822dd57000 rw-s 00000000 00:04 3539009                    /SYSV00000000 (deleted)
 7f822dd78000-7f822e278000 rw-s 12735a000 00:05 7704                      /dev/dri/card0
 7f822e278000-7f822e8d9000 rw-s 00000000 00:04 11272261                   /SYSV00000000 (deleted)
 7f822e8d9000-7f822f4b5000 rw-p 00000000 00:00 0 
....

```
but date is obsolete (Date: Fri Mar 14 20:03:18 2014 shall be today) so file might be not relevant to this issue.

What can be done?

---

### Post by TheFu on 2014-03-22
Stay patched.
Don't install software from non-repo sources.
Turn up logging levels.
Determine how to reproduce the issue 100% and submit a bug.

---

