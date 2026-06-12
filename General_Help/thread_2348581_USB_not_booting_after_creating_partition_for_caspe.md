---
title: "USB not booting after creating partition for casper-rw"
date: 2017-01-05
forum: General Help
---

### Post by morgainebrigid on 2017-01-05
I am trying to put Ubuntu Studio on a bootable live USB drive with persistence, and I want more than 4gb for the casper-rw. 
I have successfully installed Studio onto my USB stick twice now. It booted and was persistent. But the I tried to create a casper-rw partition that could be larger than 4gb, using the instructions here: [https://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](https://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)
Each time I have tried this, the USB stick was no longer bootable, although GParted said it was. 
The first time I used Live USB Install, and the second time, I used Yumi.
Any advice would be appreciated.

---

### Post by sudodus on 2017-01-05
Try with ***mkusb***. It can create a persistent live drive with a casper-rw partition automatically. See the following links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

-o-

Maybe you want to try the new mkusb version 12 alias ***dus***, which is still in the unstable repository because it is still tested. (It works well for me, and I think it will soon be released). See this link

[dus is mkusb version 12.0.0](https://ubuntuforums.org/showthread.php?t=1958073&page=30&p=13588382#post13588382)

(Otherwise use mkusb version 11 according to the first two links.)

---

### Post by morgainebrigid on 2017-01-05
Yes, both of the installers I used did that as well, and worked fine.  That's not the problem.

The problem is that when I try to make a casper-rw directory (as opposed to the casper-rw loopback they already have) so that I can have more than 4G storage space on my disk, it always makes the usb not boot anymore the next time I use it.

---

### Post by sudodus on 2017-01-05
And mkusb uses a casper-rw partition as its standard method. It just works that way. It is probably ten times faster to use a tool that makes a casper-rw partition, than to try to modify a system, that is created with a casper-rw file.

---

### Post by C.S.Cameron on 2017-01-05
Persistent partitions have not worked with syslinux installs, (Unetbootin, Universal, Rufus, SDC, etc), since 14.04.
They do work with grub2 type installs such as mkusb.
Mkusb will automatically make persistent partitions and leave remaining space NTFS so Windows can see it.
Very simple to use.

---

