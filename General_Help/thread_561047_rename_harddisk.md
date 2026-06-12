---
title: "rename harddisk"
date: 2007-09-27
forum: General Help
---

### Post by nate_nightroad on 2007-09-27
hi...my hard disk have 2 partitions,one with ubuntu 7.04 and the other is just data....now how do i rename the data drive?

the original drive name is Data...now i wan to rename it to Backup

please advice....btw the drive format is FAT32 while ubuntu is ext3

---

### Post by brettg on 2007-09-27
Disks in Linux don't have names as such. I think you are thinking of Windows disk labels which don't apply here. 

Here is a short primer on disks in Linux;

The closest thing to a disk name is the device name, which is usually /dev/hda or /dev/sda. 

This device is then mounted to a mountpoint in your system root. This mountpoint is just a simple directory, often in /mnt, and in more recent distros (including ubuntu) /media. It doesn't have to be in one of those though, I have a disk mounted to /store for instance.  

If you type df -h at the console you will see the drive devices and their mountpoints.

---

