---
title: "(Gutsy) Partition access issue"
date: 2008-04-30
forum: General Help
---

### Post by spaceboy909 on 2008-04-30
When the system boots up, one partition on the 2nd drive is not readily accessible for some reason.

The problem partition is hdd7 (ext3), just a storage partition, and the mount point is /media/disk.  This was an ex-windows partition.

The other drives/parts are shown on the desktop like normal, but not hdd7.  In nautilus, it is listed at first as "50Gb partition".

When I try to access it, I'm asked for my admin pw.  After this, the name in nautilus changes to 'disk', and it is fully accessible until the next reboot.

At first I thought it was an ownership/permissions issue, so I checked.  It showed the owner/group to be root, so I changed the group to 'user', and set 740, but I couldn't create a desktop link that way, so I set 770, and thought I had it fixed, until I rebooted.

I also see that my hdd5 drive is labeled/mounted as 'plugdev'.  Do I need to change it to that group?

Any help is appreciated.

---

### Post by bodhi.zazen on 2008-04-30
You have to manually make an entry in fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

