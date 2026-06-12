---
title: "Boot problems with 7.10 Gutsy Gibbon"
date: 2008-04-20
forum: General Help
---

### Post by shortylonglegs on 2008-04-20
I have been running Ubuntu on my laptop for several months with no problems, but just this morning I couldn't get it to boot.  I have it on a partitioned disk with XP and GRUB.  I select Ubuntu and the splash comes up.  The orange bar fills about 25% then goes to the black screen, where it says there is an error on /sda3 (my linux partition) that forced a check.  It gets about 60% done from here then a message shows about a missing or duplicate block.  After this nothing happens.  I have let it run for about 20 minutes.  Do I just need to let it run longer, or there something else I can do?  Any help would be great.

---

### Post by sekinto on 2008-04-20
Boot from your Live CD and try running
```
fsck -V /dev/<UBUNTU>
```
from a terminal. I'm not sure if you need root privileges or not, if you do there is sudo.

<UBUNTU> = whatever partition Ubuntu is on (example: hda1, hda2, hdb1, sda3, et cetera).

---

### Post by shortylonglegs on 2008-04-22
That worked. Thanks

---

