---
title: "boot up error"
date: 2008-04-27
forum: General Help
---

### Post by shdw.puppet on 2008-04-27
This is a big problem...
After I had upgraded to Hardy, got all of my settings back to the way I like them and all that crap, I rebooted. Then, about the  fifth time I rebooted, an error came up about halfway through the loading screen's progress.

/etc/init.d/rc: line 195 :/etc/default/rcS: No such file or directory error: '/etc/init.d/rc' exited outside the expected code flow. init:rcS main process (2422) terminated with status 1 /etc/init.d/rc: line 195 :/etc/default/rcS: No such file or directory error: '/etc/init.d/rc' exited outside the expected code flow. init: rc2 main process (2431) terminated with status 1

What is going on here? to the best of my knowledge, it looks like /etc/init.d/rc calls for /etc/default/rcS and cannot find it. If this is true, how on earth do I fix it? I do not wish to reinstall, as that would mean losing all of my settings and the like. But if it is necessary, I am sure there is a way to get to my files.

After I fix this, my home directory is so going on it's own partition.

Thank in advance.
shdw

---

### Post by MrNatewood on 2008-11-05
I just had the same problem.
What worked for me is booting from the live CD and creating the missing file with gedit.

I copied the settings from my laptop.
```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no
RAMRUN=yes
RAMLOCK=yes
```

save as /etc/default/rcS on your hard drive.

---

