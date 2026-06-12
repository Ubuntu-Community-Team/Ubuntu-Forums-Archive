---
title: "how to move ubuntu to another hdd"
date: 2008-04-04
forum: General Help
---

### Post by lemonlaw95 on 2008-04-04
hi.  i have 1 40gb hdd and 1 60gb hdd.  i want to move ubuntu to the 40gb drive, which will be the slave, and install gentoo on the 60gb, which will be the master.  gentoo will use GRUB, so i can put an ubuntu entry in there.  so i need to know what i need to do (files to modify, move, etc)to get ubuntu functioning again after i install gentoo.  thanks in advance.

-lemonlaw95

---

### Post by scannerdarkly on 2008-04-04
only thing i can think of is for you to image the drive and then install the image on the 40 GB.....I can't imagine that you can literally just move all the folders over and be ok.  Or just backup your stuff reinstall ubuntu on the 40 then install Gentoo on the 60.

---

### Post by justleen on 2008-04-04
you cannot just copy the disk, or do a disk-to-disk image.

The problem lies in grub. Its pointing to (for example) to /dev/hda1 to boot from.
If you do a disk to disk copy, it will still point to that device, thus booting of the old disk.

You could disk-to-disk, detach the old drive, and run supergrub / grub from a live cd.

Copying the files is an option as well, as long as you keep in mind you will have install grub on the new disk bootsector, and edit the menu.list

i wrote [this]("http://www.justleen.nl/?p=6") a while back

---

### Post by meazz1 on 2008-04-04
use remastersys to create a backup ISO / live cd and install it in the new drive.

Take a look here.

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys")

---

### Post by SpotDog on 2008-04-04
Hi, although I am a newbie, I once used Acronis to image an old SCO hdd, imaged it, copied it to a new drive and it worked just fine.  My only problem with the SCO was that original drive was 240mb and new drive was 2gb, I had to change cyl., sectors, hds, to match old drive.  Try Acronis!, it should even allow you to increase partitions sizes.

---

### Post by ghw on 2008-04-04
You can pretty much just copy the files, as long as you get all the hidden files and all the permissions and hard links are preserved -- you should probably try to keep the partition structure the same, although that's not strictly necessary -- I would use "cp -ax" on each partition (probably "/" "/home" and "/boot") -- as has been said, you then have to install grub so that the new disk is bootable -- you may also have to edit /etc/fstab on the new disk if it refers to UUIDs of the old disk or if the partitioning scheme has changed.

---

### Post by lemonlaw95 on 2008-04-04
actually i decided to back up my data and install gentoo on both drives, but i might still use this help later! (i'm always changing things like OS locations. :))  in fact, i'll save this whole page and back it up, because i'm sure i'll use it again!  thanks for all your help!

---

