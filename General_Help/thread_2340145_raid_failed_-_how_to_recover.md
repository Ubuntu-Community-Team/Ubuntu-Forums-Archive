---
title: "raid failed - how to recover?"
date: 2016-10-16
forum: General Help
---

### Post by honeycombs_big_yahyahyah on 2016-10-16
Hi all,

Home power went out a couple times (no UPS, whoops), and now my RAID *seems* to be hosed.  Hoping someone can point me in the right direction.

Upon boot, ubuntu tells me that it can't mount the /root filesystem, and the ubuntu recovery screen says that it can't access the /tmp directory.  I've managed to get into the maintenance shell.

If I recall correctly, my setup is something like below.  I have 4 3TB drives.
/       : RAID-5 
/boot : RAID-1 (I think)
/swap: RAID-10 (I think)

When I look at /proc/mdstat, the three volumes seem to be fine (all "U"s).  So maybe it's corrupted data and not a RAID problem?  In the shell, both /root and /boot are empty.  /tmp has stuff in it.

Any pointers greatly appreciated!  Thanks...

Ubuntu server 14.04


EDIT: Strangely, the system actually fully started up after a recent reboot.  It now looks like one of the disks might be having errors, but I'm not sure how to interpret what I'm seeing.  See the first image below for the error.  /proc/mdstat doesn't show any issues, however (see the second image below).  Any thoughts greatly appreciated!

[IMG]https://dl.dropboxusercontent.com/u/2215004/IMG_5965.JPG[/IMG]


[IMG]https://dl.dropboxusercontent.com/u/2215004/IMG_5966.JPG[/IMG]

---

