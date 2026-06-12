---
title: "Complete freeze when I try to mount my 500 gb hard drive!"
date: 2008-04-08
forum: General Help
---

### Post by nestcrw on 2008-04-08
So this is very frustrating. When I try to mount my 500 gb hard drive, my system freezes completely. No ctrl + alt + bksp or del. I have to hard reboot. 

This is the output of fdisk -l
> john@john-desktop:~$ sudo fdisk -l
[sudo] password for john:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0066e120

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca0e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       51877   416701971   83  Linux


I think I might be missing a swap partition? Would that do this? If so, how can I make another? 
There is very important data on this drive I can't afford to lose.

I am a seasoned ubuntu user, thats why I didn't put this in the noob section.

Any suggestions are much appreciated.

---

### Post by nestcrw on 2008-04-08
Update:

I think I made it worse. 

I tried to create a swap partition with gparted. The system locked up when I did that too. Now ubuntu won't even boot with this drive plugged in! Argh.!

---

### Post by kpkeerthi on 2008-04-08
You should run gparted from a Live CD. The partition you want resized/altered should not be mounted.

To check if you are using a swap partition, open a terminal and type **top**. That should report your swap partition size and amount of swap in use.

---

