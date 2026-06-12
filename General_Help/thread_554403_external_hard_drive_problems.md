---
title: "external hard drive problems"
date: 2007-09-18
forum: General Help
---

### Post by xGutsAndGloryx on 2007-09-18
my computer is no longer detecting my external hard drive. it doesn't give me any errors. it just never displays the icon of the screen. i checked under places and it doesn't come up there either. what should i do?

---

### Post by xGutsAndGloryx on 2007-09-18
i have also tried going to ntfs configuration tool. it gives the this error msg: Error : An error occured when trying to initialize HAL. Can't search for new partition


Update 1: I was able to perform the following steps successfully
sudo mkdir /media/sda1
sudo mount -t ntfs-3g  /dev/sda1  /media/sda1 -o defaults,umask=0
ls /media/sda1 <---- it successful mounted i was able to pull information from it.
sudo umount /dev/sda1


its still not automatically detecting the external hdd like when i first installed the os


Update 2: 
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7132    57287758+  83  Linux
/dev/hda2            7133        7296     1317330    5  Extended
/dev/hda5            7133        7296     1317298+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS
xgutsandgloryx@xgutsandgloryx-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              54G   21G   31G  40% /
varrun                220M  236K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
procbususb            220M  152K  220M   1% /proc/bus/usb

---

### Post by xGutsAndGloryx on 2007-09-19
.

---

### Post by xGutsAndGloryx on 2007-09-19
.

---

### Post by priegog on 2007-09-20
Hi. I'm by no means an expert, but since nobody is replying to you, I will try to help. I do not know how the mount commands work, so I'll try to do what I normally do when things screw up for me.
First, check under system>preferences>removable drives and media, and check that the options to automatically mount hotplugged drives is on.
But I am assuming you did not move that so it most probably IS on. 
And secondly, for me at least the partition editor (parted) did something so that my HDD could not be automatically mounted anymore. I solved this by restarting the computer while having the external hard drive turned on.
Hope that helps, but if it doesn't at least I bumped you up.

---

