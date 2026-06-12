---
title: "[Urgent Help] Hardrive not recognised and need backup"
date: 2015-10-09
forum: General Help
---

### Post by rahul39 on 2015-10-09
Hi All,

I am extremely new to Ubuntu (1st time user for past 2 hours). I have been a windows user and recently upgraded my laptop from Windows 8 to 10. Suddenly windows stopped working and all I see is a blank screen. I think this could be a bad sector / hard drive problem. I need help with the following:

a. I have precious data on old drive and I need to back it up
b. I don't have a windows installation CD so would like to retain the windows on the HDD if I can
c. I tried using Gparted and see the whole drive unallocated with an error of /dev/sda/ unrecognised disk label

I read a few answers on this forum and tried to do the following: 

sudo fdisk -l with the below output:

Disk /dev/sdb: 8100 MB, 8100249600 bytes
255 heads, 63 sectors/track, 984 cylinders, total 15820800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15820799     7909376    b  W95 FAT32


Can you please tell me what are my best options.

---

### Post by TheFu on 2015-10-09
Doesn't seem to be an ubuntu question.  I only see Windows stuff listed.

Also - using fdisk on a GPT disk is a bad idea - there are reasons. Use parted or gparted, when appropriate.

Did you disable quickboot/fastboot/smartboot - or whatever Microsoft calls it now? It is their way to not properly dismount storage partitions at shutdown/reboot. That is fine, provided you only boot 1 OS.  Not so good if you boot 2 or more.

Sorry that I cannot help more with Windows. Never touched Win8, Win9 or Win10 before.
I suspect you need to make a Windows-save-your-butt disk ASAP.

---

### Post by rahul39 on 2015-10-10
Hi,

I need help in recovering data from my harddisk. 

Regards,

Rahul Vani

---

