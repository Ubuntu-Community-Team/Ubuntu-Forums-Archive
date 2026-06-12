---
title: "How to increase size of Ubuntu disk"
date: 2022-02-05
forum: General Help
---

### Post by krishnadev on 2022-02-05
I run Windows and Ubuntu on a single disk. I allocated most the space for windows as I use it for games. But after some use space allocated to Ubuntu is almost over. So i booted to windows and reduced the volume size to create unallocated space. I saw few tutorials on how to add that to my Ubuntu partition. Some tutorials showed that after selecting resize option in 'disks' we can just move slider. But that is not working for me. Is there any other way to do it?

[IMG]https://prnt.sc/26p6ur4[/IMG]

---

### Post by Impavidus on 2022-02-05
You can't change a partition when it's mounted and you can't unmount the root partition of the running operating system. So, you have to do this from a live disk. The live disk you used to install Ubuntu already has gparted installed, which you can use to change partitions.

Partition 4 is in the way and has to be moved to the left before you can expand partition 5 into the unallocated space. As partition 4 is a Windows partition, use Windows for that. Then reboot Windows to make sure all changes are actually written to the drive, then boot your Ubuntu live disk to expand the Ubuntu partition.

---

### Post by TheFu on 2022-02-05
Shifting left is very hard. Extending to the right is usually trivial.  That doesn't help you now, but for the future, it might.

First, we cannot modify mounted partitions while they are mounted.  So, to move the existing partition to the left, you'll have to boot from a Try Ubuntu flash drive, run gparted, then try the shift-left again. The left-shift is dangerous, BTW.

But there may be an easier way. If you are using LVM on your Linux install, then accessing the newly available storage isn't too hard and has very little risk. Run this command and post the output **wrapped in code-tags** so we can learn about your storage setup:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
There's a 50/50 chance you could have a volume manager, which will make this relatively easy and risk free.

Please run the command and use code-tags. [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code-tags. Without those, it is just too difficult to read and prone to interpretation mistakes.

---

