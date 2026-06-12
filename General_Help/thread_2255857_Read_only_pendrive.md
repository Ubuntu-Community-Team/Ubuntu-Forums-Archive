---
title: "Read only pendrive"
date: 2014-12-08
forum: General Help
---

### Post by Lingadharini_Viswa on 2014-12-08
My laptop is a dual boot machine with ubuntu 14.04 and windows 8.1. Recently my pendrive encountered an error. I cannot copy files into the pendrive. It says read-only. 
I have tried changing the permission in windows and formatting. Doesnt work. 
I switched to ubuntu.
Cannot format in ubuntu also.
Tried gparted. Doesnt help.
Help me.

find /dev/sdb1 -type f -exec chmod 666 {} \;

 doesnt work.
Used fdisk -l and my drive is /dev/sdb1

sudo mkfs.vfat -n 'Ubuntu'-I /dev/sdb1

Results in:

mkfs.fat 3.0.26 (2014-03-07)
mkfs.fat: warning - lowercase labels might not work properly with DOS or Windows
mkfs.vfat: unable to open /dev/sdb1: Read-only file system

Used fsck:

fsck -n /dev/sdb1

fsck from util-linux 2.20.1
fsck: fsck.ntfs: not found
fsck: error 2 while executing fsck.ntfs for /dev/sdb1




It is in NTFS file system.
Also, I am unable to format the drive. Kindly help.

---

### Post by sudodus on 2014-12-08
When pendrives fail, they often start by getting read-only.

But there might be some other error with the partition table, that keeps you from formatting the drive.

You have tried in linux and Windows. ***Have you also tried in different USB ports and in different computers?*** Some pendrives work with some hardware and firmware, but not everywhere.

I suggest the you try to wipe the first megabyte with ***mkusb***, and after that use ***gparted*** in linux to create a new partition table, and finally try to create a partition and a file system in that partition. If it still does not work, you can conclude that it has failed beyond saving (unless you want to learn how to program the built-in interface in the pendrive, and I don't know if anybody at the Ubuntu Forums knows that kind of programming).

Install and use mkusb to wipe the first megabyte according to this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Install gparted:

```
sudo apt-get install gparted
```

Use the pull-down menu
[I]
Device -- Create partition table[/I]

and after that you can use the intuitive graphical interface to create a partition and file system.

---

### Post by Lingadharini_Viswa on 2014-12-08
gparted doesnt work. I have tried. I m trying mkusb. Dont know my way around. seems bit confusing.

---

### Post by Lingadharini_Viswa on 2014-12-08
> [COLOR=#000000][FONT=arial]You wanted to wipe a mass storage device (typically USB drive) ...
[/FONT][/COLOR][COLOR=#000000][FONT=arial]Wiping the first megabyte (MibiByte) of /dev/sdb ... :
... Failed :-([/FONT][/COLOR][COLOR=#000000][FONT=arial]


The target device is unmounted and can be unplugged.
[COLOR=#2252A0]Name: usb-SanDisk_Cruzer_Blade Dev: /dev/sdb Size: 16009MB[/COLOR]
You may need to [COLOR=#CC0000]unplug & replug the drive or reboot[/COLOR] 
for the kernel to see that the drive is wiped. 
[/FONT][/COLOR]

This was the error message I got from mkusb.

---

### Post by sudodus on 2014-12-08
This means that the low level writing of dd (via mkusb) did not work. So I think it is not only the file system that is read-only. I'm afraid that the whole drive is read-only, in other words, that it is failing. (I bought a ten-pack of Sandisk Cruzer blades (4 GB), and they are still going strong, but the lifetime of pendrives is limited.)

See [This link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426")

---

