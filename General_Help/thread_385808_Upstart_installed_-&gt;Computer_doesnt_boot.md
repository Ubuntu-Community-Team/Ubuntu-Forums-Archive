---
title: "Upstart installed -&gt;Computer doesnt boot"
date: 2007-03-16
forum: General Help
---

### Post by hithwen on 2007-03-16
Hello, today I installed upstart as replacement to sysvinit and now the computer doesnt boot, it holds in black screen with the cursor blinking at the upper left corner.
I tried to start in recovery mode to fix it reinstalling sysvinit but I get this errors:

#~aptitude install sysvinit
...
0 packages upgraded, 1 newly installed, 7 to remove an 0 not upgraded.
Need to get 0B/109kB of archives. After unpacking 79.4MB will be freed.
Do you want to continue [Y/n/?] y

[B]dpkg: unable to access dpkg status area: Read-only file system
W: Not using locking for read only lock file /var/lib/apt/lists/lock
E: /var/log/aptitude - Unable to open %s to log actions (30 Read-only file system)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Triying to recover
dpkg: unable to access dpkg status area: Read only file sysyem
W: Not using locking for read only lock file /var/lib/dpkg/lock[/B]

:confused:

---

