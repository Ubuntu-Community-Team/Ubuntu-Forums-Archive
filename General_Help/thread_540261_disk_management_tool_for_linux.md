---
title: "disk management tool for linux?"
date: 2007-09-01
forum: General Help
---

### Post by dachinster on 2007-09-01
Hi guys,
I recently was dual booting with Windows and Ubuntu
I put in my Windows XP CD and deleted the Windows partition deliberately but I did not format the partition leaving it raw and unallocated, and then booted into Ubuntu

Is there a tool available that will allow me to format the partition in ext3 WITHOUT rebooting and using something like gparted etc?

Windows XP came with a disk management utility that allowed you to view each disk and how they were broken down into partitions and then allow you to format whichever one you want.

Does Ubuntu have such a feature natively or available in the repositories somewhere?

---

### Post by Steveway on 2007-09-01
You can install gparted on Ubuntu.

---

### Post by wirelessmonkey on 2007-09-01
You don't have to boot from an external drive to use gparted, you can just run it locally, since the empty partition will be unmounted, and do whatever editing you like.

---

### Post by dachinster on 2007-09-01
thanks guys
i installed gparted and formatted the partition, but it appears as "disk"
I went into Device>Set Disklabel
but it tells me that using it will rename the entire disk and not just the partition.
How can i rename just the partition?

---

### Post by airtonix on 2007-09-02
i think partition names are actually the folder name you mount it to...

otherwise its just called by the hardware socket its plugged into..

ie: /dev/hda is ide hdd device plugged into ide socket 1.

which would be (in my imaginary world) mounted to : 

/media/NewHardDiscNameHere

hence its name would appear as "NewHardDiscNameHere" when its showing on my desktop.

p.s. i highly recommend this partition layout : 

partition-1 [ext3]:  10g for root filesystem [\]
partition-1 [ext3]:  1g for swap [linux-swap]
partition-1 [ext3]:  rest for home [\home]

so you only have to format partition-1 when you do a new OS install

---

### Post by cwaldbieser on 2007-09-02
> **dachinster said:**
> thanks guys
i installed gparted and formatted the partition, but it appears as "disk"
I went into Device>Set Disklabel
but it tells me that using it will rename the entire disk and not just the partition.
How can i rename just the partition?

The "e2label" program will let you change the label of an ext2 or ext3 partition.

---

### Post by dachinster on 2007-09-02
Hey, thanks for the info, but I am not sure I am doing it right:

dachinster@Ubuntu:~$ sudo e2label /media/disk /media/Windows
e2label: Is a directory while trying to open /media/disk
Couldn't find valid filesystem superblock.
dachinster@Ubuntu:~$

---

### Post by ingvildr on 2007-09-03
Close, but you need to do something like this 
```
$ sudo e2label /dev/XX Windows
```
Where /dev/XX is the the device/partition you want to rename, to find out what that is go into System > Administration > System Monitor then the file systems tab.

---

