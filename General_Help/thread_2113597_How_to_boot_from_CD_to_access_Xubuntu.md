---
title: "How to boot from CD to access Xubuntu?"
date: 2013-02-07
forum: General Help
---

### Post by ineuw on 2013-02-07
I have a dual boot Win XP SP3/Xubuntu v12.04 setup with the following partitioning:

sda
#1 = Primary NTSF (Win XP C: drive with Xubuntu boot)
#5 = logical NTSF
#6 = logical Ext 4 (Xubuntu)
#3 = primary Swap

XP crashed yesterday and had to be re-formatted and completely re-installed on sda1, (as it always was). In the process the boot to Xubuntu was lost. Xubuntu itself is a healthy version 12.04 installation with kernel version 3.2.0.35. Using the Xubuntu CD, the root (/) of sda6 is accessible in a shell and using "ls" the folders are accessible, but I have no idea how to start Xubuntu to access grub and reinstall multi boot on sda1.

Can anyone provide guidance? Thanks.

---

### Post by Enigmapond on 2013-02-07
This will fix your boot...
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ):P

---

### Post by JKyleOKC on 2013-02-07
Use the live CD, download Boot-Repair, install it to the live-CD session, and run it. First time around, click the "report" button rather than "recommended repair" and then use your browser to view the report it will generate (make a note of the URL for the report, which the program will show you when it's complete). At the end of that report it will tell you what it will do if you select "recommended repair" so if that doesn't indicate anything alarming, run it again and select recommended repair. Upon rebooting, you should have the grub menu back just as before.

The XP install rewrote the Master Boot Record of your hard drive, and that's why the multi-boot menu vanished. Boot-Repair will do the re-installation of the menu for you.

I don't have a link to the download site handy on this machine, but you can find it easily by doing a Google search for "Boot-Repair" and going to the most recently updated site for it. The program's author is a regular here on the forums, and keeps it up to date.

EDIT: I see someone else already gave you the link!

---

### Post by ineuw on 2013-02-09
Many thanks to you both for the help. I am replying from within Xubuntu, which is the best indication that it worked!

---

