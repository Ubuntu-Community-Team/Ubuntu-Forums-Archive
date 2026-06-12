---
title: "Can't install any packages."
date: 2007-10-04
forum: General Help
---

### Post by Madhatta on 2007-10-04
I'm running Gutsy Gibbon, and as of this morning, can't install packages. In Update Manager, it downloads properly, then gives me:

E: /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb: trying to overwrite `/usr/share/doc/libcupsys2/CREDITS.txt', which is also in package libcupsys2

This also happened earlier today with GIMP, same error message and all, I just completely removed it, thinking it was just a fluke. After throwing that error, it says Update is Complete (Even though nothing was actually installed).

Any help/ideas would be appreciated.

---

### Post by T700 on 2007-10-04
This is a confirmed bug: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/149097](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/149097) 

Only solution so far is to wait for an update.

Paul

---

### Post by Madhatta on 2007-10-04
Thanks.

---

### Post by T700 on 2007-10-04
Some people in this thread seem to have found a solution: [http://ubuntuforums.org/showthread.php?t=567408](http://ubuntuforums.org/showthread.php?t=567408)

---

