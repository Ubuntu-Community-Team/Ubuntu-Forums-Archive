---
title: "How to format my external hdd"
date: 2008-01-16
forum: General Help
---

### Post by AlexFirth91 on 2008-01-16
It has linux on it but I want to delete it windows does not recognize it and I cant boot it HELP PLEASE!!

---

### Post by Cr0n_J0b on 2008-01-17
do you have a linux system still?  If so, then use fdisk on the linux system and set use the "t" option to toggle the disk type to Fat32 or something like that.

When faced with a similar issue, I just downloaded Knoppix linux and burned the CD.  boot from that and then do the format business, works like a charm.

If you want to boot from the drive make sure to set the bootable flag in fdisk.

---

### Post by Technophobia on 2008-01-17
try downloading a Linux tool called **gparted**. This will allow you to format the drive and play with partitions. In your case you can just delete the whole partition leaving a raw drive. Hope this helps and good luck.

---

### Post by cdaringe on 2008-01-17
all previous mentioned suggestions would work well.
chances are as an ubuntu user you have the ubuntu live cd. pop that little guy in and boot from it.  from here you can access or install gparted.  it should already be on there i believe.  open it, and you can locate your usb drive. it has a friendly gui, so formatting it should be fairly easy. tell us how it goes.

---

### Post by xyphur on 2008-01-17
on top of all the above methods, which will work, you can do it in windows as well... just not in the same manner as you're probably used to.

Right click My Computer > Manage

Click Disk Management on the left pane, right click the drive's graphical partition representation in question, 'Delete Partition..." Then right click it again and create a new partition. A wizard will start and present you with options on the size and type and allow you to assign it a drive letter and whatnot.

Alternatively, I usually pop my Hirens Boot CD in and use one of the MANY partition utilities on it for these sorts of tasks... saves me from having to wait for redundant things to load in either Linux or Windows... if all I'm doing is working on a hard drive, I don't need sound/video/network drivers loading... waste of time. :)

Hope that helps.

---

### Post by AlexFirth91 on 2008-01-21
thanks about to try now

---

### Post by AlexFirth91 on 2008-01-21
thanks it worked

---

