---
title: "Help with permissions"
date: 2007-04-29
forum: General Help
---

### Post by r5gtt2k3 on 2007-04-29
Totaly new to ubuntu, Currently running ubuntu 7.04 feisty, Im trying to add files to my hard drive but a window pops up with "blah blah blah You do not have permissions to do this" now ive looked everywhere in ubuntu but cant find anything to do with it, ive gone into my user account and everything is ticked, Does anyone know how to solve this problem please, Thanks

---

### Post by Enfenion on 2007-04-29
What kind of file system is on the disk?
Is it an internal or external drive?

---

### Post by r5gtt2k3 on 2007-04-29
It is an internal IDE drive

---

### Post by Enfenion on 2007-04-29
With what kind of file system?

check using:
```
fdisk -l
```

---

### Post by r5gtt2k3 on 2007-04-29
Sorry to be a pain but what is fdisk -l ? how do i check it with it :confused:

---

### Post by Enfenion on 2007-04-29
start a terminal (from Applications->Accessories->Terminal)
write "sudo fdisk -l" (without the quotes) and press enter

---

### Post by r5gtt2k3 on 2007-04-29
Thank you here is what it said :confused: 
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Enfenion on 2007-04-29
Hmm... looks like you have an old version of fdisk...
Write "fdisk -v" to check you version...

Try to do this:
```
sudo apt-get update
sudo apt-get install fdisk
```

then try:
```
sudo fdisk -l
```
again...

---

