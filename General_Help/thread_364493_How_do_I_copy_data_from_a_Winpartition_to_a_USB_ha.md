---
title: "How do I copy data from a Winpartition to a USB harddrive using Ubuntu 6.10 Live CD"
date: 2007-02-18
forum: General Help
---

### Post by Onaka on 2007-02-18
As title says I have some computer problems with XP. I dosent want to start. 
And I realy need to make a backup on some files on the C: partition. 

How do I copy files from my C-drive to USB-harddrive?

This is how my computer is configurated at the moment. 

2 HDD's. On the first HDD I have 4 Partitions. Windows,SWAP, Fedora Core (but it dont want to start), HP rescue harddrive. 

I need to get files from my Documents and Settings folder more specific my pictures folder.

I got the following Live CD's 
DSL (Damn Small Linux)
Ubuntu 6.10 
Ubuntu 6.06


I'm not good in Linux environments so I need detailed help..

---

### Post by chinese_ys on 2007-02-18
use live cd to boot up, and mount the win drive, hope it it fat32 partition. Then copy you files.

live cd should recognize your usb drive.

---

### Post by solar george on 2007-02-18
Boot up one of the ubuntu cds 

You should see a icon for your harddisk on the desktop. Double click on it to open it. 

Insert your usb disk - it should open automatically in annother window.

Use drag and drop to copy files over.

---

### Post by Onaka on 2007-02-18
I dont have an icon for my harddrive on the desktop. Only Install and Example catalog. 

How do I type to mount my drive? In GParted I can see the partition I want to access can I do anything in GParted so that I can see my files on the /dev/sda1/ ?

---

### Post by solar george on 2007-02-18
> /dev/sda1/ ?

Is this the C: drive or the USB drive. 

It doesn't make any difference to process for mounting it though.

```
$ sudo mkdir /media/sda1
$ sudo mount /dev/sda1 /media/sda1
```

This will mount this particular disk. You will need to be root to access it though,

```
$ sudo nautilus
```
Will open a file manager as root.

You will then need to repeat the process to mount the other disk. Just replace sda1 with the correct device. 
If sda1 is the C: drive you will probably find that the USB disk is mounted automatically.

Just drag and drop to copy  files from one to the other.

---

### Post by Onaka on 2007-02-20
thank you.. I will test it when I get back home.. :)

---

