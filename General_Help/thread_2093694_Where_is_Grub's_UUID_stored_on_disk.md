---
title: "Where is Grub's UUID stored on disk?"
date: 2012-12-11
forum: General Help
---

### Post by workdone6789 on 2012-12-11
I am still confused where to look for UUID on disk ...I have a disk and i want to read it's uuid by hexeditor...

---

### Post by oldos2er on 2012-12-11
Post moved to its own thread.

---

### Post by Herman on 2012-12-11
> I am still confused where to look for UUID on disk ...I have a disk and i want to read it's uuid by hexeditor...     There are UUIDs (Universal Unique IDentifying (numbers) located in different places in the computer. 

There is a MBR 'Disk Identifier' which is a 4-byte random number that is automatically generated when the MBR is first written. You can use a hex editor to examine your MBR if you wish. As far as I know, GRUB does not use the MBR Disk Identifier but the Windows Vista and 7 boot loaders are tied to this number, (probably as one of their anti-piracy measures I guess). If the MBR 'Disk Identifier' gets changed for any reason, Windows won't boot but Ubuntu will continue to boot regardless.

 The file system UUID numbers (not the MBR Disk Identifier), are used in GRUB and also in Ubuntu's /etc/fstab file to keep track of the various file systems in the different partitions. 
The file system UUID numbers can most easily be viewed with the blkid command, we don't need a hex editor for those. 
```
sudo blkid
```

---

### Post by Herman on 2012-12-11
Filesystem UUID numbers are located with the rest of the file system metadata in the superblocks for the ext4 file system.
If you want to take a look at the humanly readable part, use dumpe2fs with the -h option,
```
sudo dumpe2fs -h /dev/sda1
```Where: /dev/sda1 is a partition which contains an ext series file system 

Normally the file system UUID numbers are changed automatically only when a  partition is formatted with a new file system. 
It is rarely necessary to need to change a file system UUID number except when an operating system or other partition has been cloned and then there could be two file systems with the same UUID present in a machine. It is possible to  edit one of them using tools relevant to the particular  file system, and then GRUB and /etc/fstab files will need updating to match.

---

