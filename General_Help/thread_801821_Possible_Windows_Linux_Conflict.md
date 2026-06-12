---
title: "Possible Windows Linux Conflict"
date: 2008-05-20
forum: General Help
---

### Post by Reg Editor on 2008-05-20
When the computer boots from the Windows XP CD,it hangs (a black screen) after "Setup is inspecting your computer's hardware configuration".It happens with either of the 2 CD drives,and with a copy (previously tested and OK) of the XP CD.
With a google search,a lot of the results point to multi-booting Windows and Linux as somehow the cause of the problem.
I have  XP installed on each of 2 partitions; Ubuntu; and Mint.
Since the 2 Linux installations,I have done a clean install of XP on the 2nd partition.

Some days ago using Mint I noticed that one of the volumes (the clean install of XP) was not showing in "Computer".After googling for a solution I used a "mount"command,that didn't make the 2nd XP volume appear under "Computer" immediately but since the the next day the volume has been  showing  although it's name is  "Volume: disk" instead of "Volume: hda5" (GParted shows it as hda5 with the mountpoint as /media/disk instead of /media/hda5).

The Ubuntu Live CD can be used,no issues with that.

It seems something I have done has caused the "Setup is inspecting ....." problem.

All advice welcomed

---

### Post by lemming465 on 2008-05-21
If you post the output of *fdisk -l* we may be able to comment more intelligently.  In general, you can have fairly complex mixtures of windows and linux and other stuff in multiboot configurations.  I've had as many as five different installs of windows on a single PC along with multiple linux installs without trouble.

One way to cause trouble: have more than one primary FAT32 or NTFS partition on a single disk.  If you have one primary windows partitions and the rest logical things will behave better.

---

### Post by Reg Editor on 2008-05-23
Thanks for your reply.I'm using Mint at the moment.

FORTUNE PROVIDES QUESTIONS FOR THE GREAT ANSWERS: #13
A:      Doc, Happy, Bashful, Dopey, Sneezy, Sleepy, & Grumpy
Q:      Who were the Democratic presidential candidates?
owner@owner-desktop:~$ fdisk -l
owner@owner-desktop:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
owner@owner-desktop:~$ fdisk /dev/hda 

Unable to open /dev/hda
owner@owner-desktop:~$ fdisk /dev/hda1

Unable to open /dev/hda1
owner@owner-desktop:~$ fdisk /dev/hda7

Unable to open /dev/hda7
owner@owner-desktop:~$ 

What have I done wrong?


I've attached a GParted screenshot.


I've discovered the computer won't boot from a Microsoft MS-DOS Startup floppy disk either.

---

### Post by fjgaude on 2008-05-23
You must be root to use fdisk:

```
sudo fdisk -l
```

should do it.

---

### Post by Reg Editor on 2008-05-23
Thank you.

Things past redress and now with me past care.
                -- William Shakespeare, "Richard II"
owner@owner-desktop:~$ sudo fdisk -l
[sudo] password for owner:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f3f1f3f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/hda2            2806        4998    17615272+   5  Extended
/dev/hda5            2806        3659     6859723+   7  HPFS/NTFS
/dev/hda6            3660        3721      497983+  82  Linux swap / Solaris
/dev/hda7            3722        4329     4883728+  83  Linux
/dev/hda8            4330        4391      497983+  82  Linux swap / Solaris
/dev/hda9            4392        4998     4875696   83  Linux
owner@owner-desktop:~$

---

