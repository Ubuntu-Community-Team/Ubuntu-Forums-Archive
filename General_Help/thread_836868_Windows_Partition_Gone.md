---
title: "Windows Partition Gone"
date: 2008-06-21
forum: General Help
---

### Post by moldy on 2008-06-21
Hi

I think i've stuffed my windows partition. Everything was working fine.  Then I accidentally let Azureus fill up my windows drive until there was 0 bytes left.  100% full.

Still everything was ok - until I rebooted.  Now I get the dreaded blue screen when I try to boot into windows, and my links to folders on the windows partition are all broken (it is not mounting and it is my storage partition).

Does anybody know how I can get access to specific files on that partition and delete them to free up some space?  I think that's all I need to do, but am unsure.  I can't even get into windows safe mode...

thanks in advance, moldy.

---

### Post by tamoneya on 2008-06-21
so that we can familiarize ourselves with your computer and partitioning scheme please post the output of:```
sudo fdisk -l
```  Also if you could post whatever errors you receive when you attempt to mount.

---

### Post by smo0th on 2008-06-21
lol.. good one, try ```
sudo mount -t ntfs-3g /dev/sdb5 /media/windows -o force
``` using your proper device and mount point

---

### Post by moldy on 2008-06-21
thanks for the quick reply tamoneya. the output from fdisk is:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        6079    48789405    7  HPFS/NTFS
/dev/sda3            6080        6201      979965   82  Linux swap / Solaris
/dev/sda4            6202        7296     8795587+  83  Linux

When I try and click on one of my links to the windows partition I get:

The link to "Pictures" is broken. Do you want to move it to the garbage bin.  This link can't be used, because its target "/media/windows/Documents and Settings/richard/My Documents/My Pictures" doesn't exist.

Forgive me, I'm unsure what I need to type at the command prompt to mount the partition manually.  if you could tell me i'll get back immediately with the response.

moldy

---

### Post by tamoneya on 2008-06-21
go into terminal and try this command.  It is basically what smooth suggested just tweaked for your system settings:```
sudo mount -t ntfs-3g /dev/sda2 /media/windows -o force
``` This should be done in terminal(applications-> accessories -> terminal)

---

### Post by moldy on 2008-06-21
thanks guys. the output is:

$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

i tried clicking on one of my links to the partition, and the following error come up:

could not display "/home/richard/Documents".
The location is not a folder.

that error display box is now stuck on my screen! the ok button doesn't do anything!!

---

### Post by moldy on 2008-06-21
i take it back. my links now work and the windows partition is back - thanks for all your help guys. 
that's why think forum is so great. a problem that is a nightmare to me is so easy for someone else to fix - and people are so generous with their knowledge! thanks.

---

