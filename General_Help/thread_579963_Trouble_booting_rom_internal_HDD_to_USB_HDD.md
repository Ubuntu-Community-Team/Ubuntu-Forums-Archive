---
title: "Trouble booting rom internal HDD to USB HDD"
date: 2007-10-18
forum: General Help
---

### Post by chadbst on 2007-10-18
Hello folks,

I just finished installing Ubuntu Fiesty Fawn using the alternate CD on my external USB hard drive.  I used the instructions at [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB) to make a boot CD to boot into Linux.  These instructions are for people who have BIOSes that won't don't have support for booting USB drives.  I have such a BIOS

I then wanted to find a way to have Grub boot from the internal harddrive; so I created a 39MB FAT32 partition.  I then booted into Ubuntu using the CD that I created.  I did a "grub-install /dev/sda1" to install grub on the 39MB partition. I verified that /dev/sda1 is the 39MB by looking in GParted.  When I boot up, GRUB just says "hard disk error."  That is exactly what it says - without any more detail.  

So, I booted again into Ubuntu using my boot CD.  I did a "grub-install '(hd0,0)' " to install it to the MBR of the internal drive.  When I boot up, it give grub error 21.  Just for troubleshooting purposes, I tested to see if I could boot using the kernel and initrd files in the mbr.  I used the CD, changed root to hd0,0 and used the kernel - with root= set for my usb drive - and the initrd files to  boot into Ubuntu.  It worked.  That suggests to me that there is nothing wrong with the kernel and initrd files in the MBR.


Having said all that, here is my question: can I install grub on the internal HD and have it boot to the USB drive.  If so, how.  I appreciate any help

---

