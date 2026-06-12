---
title: "Missing Ubuntu's entry in GRUB"
date: 2007-03-06
forum: General Help
---

### Post by vnt87 on 2007-03-06
I just recently screwed up the permission settings in my Edgy to an unrecoverable point, so I had to make a clean install.
The re-installation process went smoothly but after restarting, the GRUB screen only shows me 2 entry: the Ubuntu memtest, and Windows XP (which I had installed on a different partition). There were no entry with the kernel version which I often see when booting into Ubuntu. I wonder how I can add them back.
Sorry for my broken English, hope you can understand what I mean.

---

### Post by Jimmey on 2007-03-06
Boot the LiveCD again.

Check to see if it automatically mounts your current Ubuntu drive (can't remember if it does, or not).  To do this, 
> fdisk -l
Figure out which one is your Ubuntu partition. Say, /dev/hda2.

To check if that's mounted, see if 
> mount | grep /dev/hda2 returns anything (replace hda2 with whichever disk/partition combination you have). If it does, you're all set. If not:

> sudo mkdir /media/ubuntu1 && sudo mount /dev/hda2 /media/ubuntu1
Again, replace hda2 with whatever works.

Once it's mounted, if it wasn't already, then you can begin work.

To edit the menu, 
> gksudo gedit /media/ubuntu1/boot/grub/menu.lst.

Then you might want to read help.ubuntu.com up on about how to add an entry.

---

