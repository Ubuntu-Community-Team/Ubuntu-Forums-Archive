---
title: "Ubuntu 8.o4 Error 15 Lost file Please Hep !"
date: 2008-06-20
forum: General Help
---

### Post by victorash on 2008-06-20
After runnning Ubuntu 8.04 from a Live CD, I decided I would install it. I went through the whole install process it partitioned the disk I choose how Much Room for Windows and Ubuntu . Everything seemed to work fine. It rebooted Ihad the options of loading into Windows or Ubuntu, I choose Ubuntu it starts to load The comes up with the folllowing Error Message:

Error 15 File not found. How do I find that File (is this referring to Ubuntu itselfe ? ) Becuase I spent a lot of time installing something. Is there information I can supply that will help find this File ?  I have tried the 32bit and 64bit versions and results are the same..

My Computer Details:

Windows XP Professional
intel(R) Core (TM)2 CPU
6400 @ 2.13Ghz
2.14 GHZ, 3.62 GB of Ram

Processors
2x Intel(R) Core(TM)2 CPU 6400@2.13GHZ

Thanks Alan

---

### Post by dracayr on 2008-06-20
In the menu on startup, select the ubuntu entry and press e. post what it sais there.

dracayr

---

### Post by victorash on 2008-06-20
> **dracayr said:**
> In the menu on startup, select the ubuntu entry and press e. post what it sais there.

dracayr

Selecting Ubuntu

Counting down  To Menu

Then it says : 

Booting “Ubuntu” 8.04, kernel 2.6.24-16-“generic” Filesystem type is ntfs, Partition type 0x7
kernel  /boot/vmlinuz-2.6.24-16-generic root=UUID=A2cce329cce2f687 disks/root.disk ro quiet splash

Error 15: File not Found

Press any Key to continue

It come with :

Top line Says :

GRUB4DOS 0.4.3 2008-04-23, Memory: 639K / 3710M, CodeEnd: 0x412EO

Below this is the Following Options :

Ubuntu 8.04 kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.2.24-16-generic (recovery mode)
Ubuntu 8.04, memtest 86+
Other operating Systems
Microsoft  Windows XP Professional


The following messages were displayed when I when I click on each option

Ubuntu 8.04 kernel 2.6.24-16-generic

Booting “Ubuntu” 8.04, kernel 2.6.24-16-“generic” 
Filesystem type is ntfs, Partition type 0x7 kernel  /boot/vmlinuz-2.6.24-16-generic root=wie=A2CCE329CCE2F687 disks/root.disk ro quiet splash
Error 15 File not found


Ubuntu 8.04, kernel 2.6.2.24-16-generic (recovery mode)

Filesystem type is ntfs, Partition type 0x7 
kernel  /boot/vmlinuz-2.6.24-16-generic root=UUID= A2CCE329CCE2F687 disks/root.disk ro single
Error 15 File not found
Ubuntu 8.04, memtest 86+

Booting Ubuntu 8.04, memtest 86+
Filesystem type is ntfs, Partition type 0x7 
kernel  /boot/memtest86+.bin
Error 15 File not found


Thanks Hope ther might be something in there that helps.

---

### Post by dracayr on 2008-06-20
well the first strange thing I noticed is: Filesystem ntfs? on linux? not damn likely. I don't know if it even is possible. Did you choose ntfs on purpose, or is it an error (if you have no Idea what ntfs is, then it's an error)? 

well either the partition table is messed up and the partition is marked as ntfs even though it isn't (but if I recall correctly, I think that should be error 17), or grub is loading from the wrong disk. In the menu, press c. A grub prompt ("grub>") should appear.
type this:
```
find /boot/grub/stage1
```
and hit enter If that doesn't output anything, type
```
find /grub/stage1
```
and hit enter. One of the commands should output sth. like "(hdx,x)". write down the output and press esc. select the ubuntu boot option in the menu and press 'e'. replace the (hdy,y) with the output you got before, (hdx,x). press enter and then b. If all went well, post again here before you shut down the computer (unless you want to go through that process again).

dracayr

---

