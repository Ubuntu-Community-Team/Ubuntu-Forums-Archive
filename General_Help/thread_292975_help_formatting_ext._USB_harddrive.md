---
title: "help formatting ext. USB harddrive"
date: 2006-11-04
forum: General Help
---

### Post by syxbit on 2006-11-04
i don't know how to do it with "fdisk" i'm not that good reading the man pages, but i know how you are supposed to do it withi GParted.
i just unmount,delete the partition, and create a new one with ext.3
problem is, while formatting it, it seems to mount the drive halfway through, giving an error.](*,) 
what do i need to do

---

### Post by matthewstory on 2006-11-04
sudo umount /media/MYUSBDRIVE
sudo fdisk /dev/whatevermydeviceis
d
<number of partition if there is only one it will delete it automatically>
n
p
1
w
sudo mke2fs -j /dev/whatevermydeviceis

That should do the trick.

---

### Post by matthewstory on 2006-11-04
my bad . . . last line should be:

sudo mke2fs -j /dev/whatevermydeviceis1

---

### Post by jordilin on 2006-11-04
try using gparted from a linux live cd. I always do that to prevent mounts.

---

### Post by MWAAAHAAA on 2006-11-04
'cfdisk' is also a nice command line tool. Not as cryptic as 'fdisk'.

---

