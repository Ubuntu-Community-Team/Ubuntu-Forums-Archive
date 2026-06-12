---
title: "Removing windows completely from Ubuntu dual boot"
date: 2014-12-21
forum: General Help
---

### Post by Ankush_Menat on 2014-12-21
My current hard disk looks something like this. I want to remove windows completely. How to do it without messing any partitions. Can this cause issue because linux partition is at "end" or something?[IMG]http://i.imgur.com/7eInMe5.png[/IMG]
[IMG]http://i.imgur.com/5IlxBYI.png[/IMG]

---

### Post by carl4926 on 2014-12-21
In honesty
I'd backup your files 
Wipe the HDD
And start again

It is possible to format the windows spaces and shrink them back to near zero, (leaving them in place though so the partition table is the same)
Then resize all your linux
But it's very time consuming and some people might find it confusing

---

### Post by DuckHook on 2014-12-21
> **carl4926 said:**
> ...I'd backup your files 
Wipe the HDD
And start again...+1

---

### Post by nigel-antonio-pg on 2014-12-21
May I suggest you something?
Make a back up of the important data and don't be afraid of getting your hands dirty with the partitions. The worst case scenario is that you erase all the information, but if you already have a back up so it doesn't matter. You will have to invest a couple of hours of your time and make mistakes, (every one does the first time) but you will learn a lot about partitions and how they work. That's how things work in Linux: you can do anything with it, but you have to make mistakes to learn.

---

### Post by Impavidus on 2014-12-21
You could simply delete the Windows partitions without touching the extended partition with Ubuntu inside. Then you can create a new ext4 partition there and use it as additional storage space for Ubuntu. Run```
sudo update-grub
```to remove Windows from the grub menu. Add a line to /etc/fstab to mount the new partition automatically. It has the disadvantage that both partitions will be so large that they are only useful if used for general file storage (media files most likely, as only with these (or with scientific data sets) you can fill tens of GBs), but those files will be spread over different partitions and therefore different directories. You won't get this diadvantage if you make a fresh start

Or you could use the disk space to install an additional Linux system. It seems you don't need the space for general storage (yet). Many people dual boot the latest LTS and the latest interim release of Ubuntu, or the development version.

---

### Post by pqwoerituytrueiwoq on 2014-12-21
You can simply do what impadidus suggested
*unless you have a pile of system customiations done you can do what carl/duckhook suggest
next next simple thing do do would me delete your swap partition and make a new one at the start of the drive (not that you need one at all with 6GB ram, also a hdd is fastest at the start so if you ever have to really on swap it will suck but suck less)
you would then note your new swap UUID and change the old one in /etc/fstab
then you can grow your root partition
you now have 2 choices 
1. clone your root fs to a new partition that you can make in the old windows space (if you skip the delete steps you can clone a linux hdd like this)
 * Boot a live usb/cd
 * simply make a new ext4 partition in your empty space
 * mount both ext4 file systems
 * run [FONT=courier new]cp -av /media/ubuntu/oldUUID/* /media/ubuntu/newUUID/[/FONT]
 * delete old root partition (the NEXT 2 stemps make the new one bootable)
 * Update [FONT=courier new]/media/ubuntu/newUUID/etc/fstab[FONT=arial] and [/FONT][/FONT][FONT=courier new]/media/ubuntu/newUUID/boot/grub.cfg[/FONT] with the new UUID
 * run [FONT=courier new]sudo grub-install --force --no-floppy --boot-directory=/media/ubuntu/newUUID/boot/ /dev/sda[/FONT]
* use gpatrted to make your file system bigger after you delete your now empty extended partition
2 make a new partition for data (eg /home)
 * eg mount the new one as /home/ankush/Videos via fstab

---

