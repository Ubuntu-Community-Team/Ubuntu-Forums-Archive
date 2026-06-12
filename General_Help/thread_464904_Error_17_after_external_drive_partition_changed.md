---
title: "Error 17 after external drive partition changed"
date: 2007-06-05
forum: General Help
---

### Post by christopher123 on 2007-06-05
First, thank you in advance for your help, and to those of you whose posts have already helped me in the past.

I am new to Linux, and have a dual install of Ubuntu 6.06 with Windows XP (for pda usage primarily). Recently I attempted to partition an external hard drive (containing only music/video/documents) from what was initially a pure NTFS drive into a split NTFS & ext 2. I did this with partition magic in xp. After turning off my computer, I then tried to restart and was told: error 17 and could not log on to grub page or either operating system. With much frustration, I eventually managed to find super grub disk, create it, and re-install grub to where it needs to be. 

So now when I turn on the computer, it goes to the grub menu, and from there, if I select xp os, it works, but if I select ubuntu, it reads the following:

[U][I]Booting 'Ubuntu, kernel 2.6.15-28-386'
root (hd0,8 )
Filesystem type unknown, partition type 0x82
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/sda9 ro quiet splash

Error 17: cannot mount the selected partition

Press any key to continue[/I][/U]



When I run off live CD and go into terminal (as recommended on other forums), I can pull up the following info, which hopefully means something to you, although it doesn't mean much to me:



[U][I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2533    20346291    7  HPFS/NTFS   -------------------11 of 19.4GB used
/dev/sda2            2534       14593    96871950    f  W95 Ext'd (LBA)--------------
/dev/sda5            2534        5083    20482843+   b  W95 FAT32-------------------
/dev/sda6            5084       11788    53857881   83  Linux---------------------------
/dev/sda7           11789       12834     8401963+  83  Linux-------------------------- 
/dev/sda8           12835       13471     5116671   83  Linux----------------------------
/dev/sda9           14339       14593     2048256   82  Linux swap / Solaris----------
-----------------------------------------------------------------------------------------------


Disk /dev/sdb: 1088 MB, 1088421888 bytes
32 heads, 63 sectors/track, 1054 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1054     1062400+   b  W95 FAT32

[/I][/U]


I believe that the problem I've had is that all partitions have been re-named/re-numbered in the creation of a new partition, so that the grub system cannot find where the linux boot system is. I'm quite sure that this is a very simple problem that could be resolved in a few lines of terminal, and I have probably spent 6 or 7 hours searching forums for exactly what to do, but with no luck so far..  If anyone has any suggestions, they would be very much appreciated.  

My experience so far with ubuntu has been great, but one thing I've noticed is that unlike other operating systems I've used, often when something goes wrong in ubuntu, it ends up making the entire system unusable, and without any friends who are experts to turn to, for me that then often results in many hours of searching internet forums and user manuals for answers to simple 30 second questions... On principle, however difficult I'm finding some things in linux, I agree strongly enough with the open-source/community sharing philosophy that I want to keep trying to get on top of it. Please help before I tear out my hair in frustration...?? 

Thanks,
Chris.

---

