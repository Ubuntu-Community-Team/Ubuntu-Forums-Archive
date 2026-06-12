---
title: "Error opening device"
date: 2013-02-01
forum: General Help
---

### Post by bj44 on 2013-02-01
When I attempt to "Create Disk Image" of a partition via Dash Home + Disks + More Actions (on that specific partition) I get the following Error.

Error opening /dev/sda5: Device or resource busy (udisks-error-quark, 0)

Any idea what am I doing wrong?

TYIA!

---

### Post by Bashing-om on 2013-02-01
bj44; Hi !

What results with the partition (un)mounted ? If "sda5" is not a system partition for the os:
```
sudo umount /<mount point>/<named directory>
```as in > sudo umount /mnt/backup where this mount point is at the directory "/mnt" accessed through the directory "/backup" Created with:
```
 sudo mkdir /mnt/backup
sudo mount /dev/sda5 /mnt/backup
``` ( too much info ???)
If the partition is mounted via the "/etc/fstab" file, the mount point is listed there.

Else: Try to image from a liveCD such that the partition is also not mounted.

[INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT]

---

### Post by bj44 on 2013-02-01
Thanks Bashing-om,
Yes, it does work for none OS partition, going to do the OS partition via Live CD next and see if that works.

---

### Post by Bashing-om on 2013-02-01
bj44; You'r look'n good !

Awaiting confirmation that all is "working" as desired.

---

### Post by bj44 on 2013-02-01
Hi Bashing-om, it worked perfect Thanks for your help. Now it is much easier to restore my system and data in case of a HDD failure.

---

### Post by Bashing-om on 2013-02-01
bj44; You do good work.

Please mark this thread as "solved" in thread tools....aids others seeking a similar solution as well as the forum aides' time are not miss directed.

[INDENT][INDENT]happy ubuntu'n
[/INDENT][/INDENT]

---

