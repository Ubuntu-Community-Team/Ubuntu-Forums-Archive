---
title: "Help ubuntu 6.10 system backup"
date: 2007-03-28
forum: General Help
---

### Post by jvan on 2007-03-28
Real noobe really needs help.

Really like ubuntu and would like to tinker with it without losing the considerable effort I've put into it now.

It won't be useful to me though if I can't do a complete backup and restore.

I've tried Mondo but it gives me a kernel Panic not syncing error when I attempt to boot.
I've tried partimage but can't get to the partition I want to save the image on when using the live CD or Systemrescue CD.
 
I've been snooping around the forums for hours. Still can't achieve my goal.

Please help. Don't want to give up on ubuntu.

---

### Post by Scunizi on 2007-03-28
Well if you're an adventurist at heart I've been able to do great backups for both windows and Linux with the "Personal Backup Appliance"  located at [http://www.vmware.com/vmtn/appliances/directory/321](http://www.vmware.com/vmtn/appliances/directory/321).  You'll need to install VMware server and burn a cd as per instructions.  After that it's pretty much a no brainer.  Works great with an external usb HD too.

---

### Post by jvan on 2007-03-28
Hey! 

That was my first response. Thanks.

As I indicated, I'm a real noob. Don't know what VMware is. Went to site suggested and still don't what it is.

I do appreciate the response. Thanks again.

---

### Post by Scunizi on 2007-03-28
VMWare allows you to run a different operating system inside of a window on your computer.  You can use it to run almost anything with some limitations.  Personal Backup Applaince is a Linux based system predesigned to do what it says.  I use it and also Win. 2k Pro in a window when I need to.  Makes things rather convienent.

---

### Post by jvan on 2007-03-29
VMware sounds like it may be a good replacement for Wine also. I am trying partimage again. If it works OK; if not may try VMware.

Thanks again

---

### Post by laidback on 2007-03-29
I use a USB hdd (250Gb) and copy the entire system over with Gparted which I have on a Live CD. It's also on the Ubuntu Live CD.
From these copies I can (and have) created clones, I can also search the backups as they're online via my USB hdd. I can check back through the versions at will, they'll all online at once.
My installation is around 10Gb so each backup takes up this amount of space too. Not a problem then to store 3 copies on a 250Gb drive. The copy takes 24mins to complete.

Kindest regards
Laidback

---

### Post by jakev383 on 2007-03-29
> **jvan said:**
> Real noobe really needs help.

Really like ubuntu and would like to tinker with it without losing the considerable effort I've put into it now.

It won't be useful to me though if I can't do a complete backup and restore.

I've tried Mondo but it gives me a kernel Panic not syncing error when I attempt to boot.
I've tried partimage but can't get to the partition I want to save the image on when using the live CD or Systemrescue CD.
 
I've been snooping around the forums for hours. Still can't achieve my goal.

Please help. Don't want to give up on ubuntu.

So don't give up. It's going to be work. Anyone who tells you different will be lying. I haven't tried it yet, but look at this link:
[http://www.ubuntuforums.org/showthread.php?t=360283&highlight=backup+restore](http://www.ubuntuforums.org/showthread.php?t=360283&highlight=backup+restore)
I'm getting ready to try it myself, since I need to resize my swap.
Good luck!

---

### Post by jvan on 2007-03-30
By Jove, I've got it!

Was able to finally achieve the backup and verify a restore. Used he SysRescue disk and Partimage. Turns out my understanding of where the mount point for the image file was wrong.

Too bad Mondoarchive doesn't work though - this would be sooo easy.

Thanks for all the help people. Good to know that there interested people willing to help out there.

---

