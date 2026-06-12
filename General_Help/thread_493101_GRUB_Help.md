---
title: "GRUB Help"
date: 2007-07-05
forum: General Help
---

### Post by fgrantham on 2007-07-05
I'm not sure if this is the proper place for this. My GRUB file has become corrupted. When I try to boot I'm getting a ERROR 22 message. How do I access the GRUB file and edit it so I'm able to boot. I'm running KUBUNTU FEISTY FAWN. It's been working well for some time now and I have just started to encounter this problem.

---

### Post by confused57 on 2007-07-05
Here's some possible solutions for grub error 22:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

You might want to mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Post the output of "sudo fdisk -lu", /boot/grub/menu.lst, and /etc/fstab...the link above has instructions on how to access your root partition, using the live cd.

---

### Post by dreadlord_chris on 2007-07-05
the easiest way would probably be to boot the LiveCD, mount the partition containing /boot - from there you can edit **/boot/grub/menu.lst**

> 
ERROR 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.


---

