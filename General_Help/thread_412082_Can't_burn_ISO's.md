---
title: "Can't burn ISO's ???"
date: 2007-04-17
forum: General Help
---

### Post by shane2peru on 2007-04-17
Ok, I have an LG burner.  I have tried K3B, Gnome-Burner (very so lacking), and Brasero to try and burn an ISO.  They seem to delete disks fine, and when I insert the cd after being burned it has data on it, so it burns something to the disk.  I have tried several different CD's and have used the CD's before (CDRW's)  I know you can burn an ISO to them, and boot of them, I have done it before.  I have never done this with this computer though.  I also am using Fiesty.  Like I said it is a new computer and I have never burned an iso and booted off of it on this computer.  I know the ISO is good I checked it md5sums and mounted it with VirtualBox and booted off the iso itself fine.  So one of two things, 1.  It is not making the CD bootable.  2.  It is not burning correctly to the CD.  Does anyone have any ideas on how to troubleshoot this?  I don't know the first place to start here.  Help!  Thanks!

Shane

---

### Post by taurus on 2007-04-17
Have you checked the BIOS to make sure you have CD-ROM first in the boot order?  If the CD boots on another machine but not this one, then the first thing you want to look at is the boot order in the BIOS.

---

### Post by shane2peru on 2007-04-17
> **taurus said:**
> Have you checked the BIOS to make sure you have CD-ROM first in the boot order?  If the CD boots on another machine but not this one, then the first thing you want to look at is the boot order in the BIOS.

Tarus, that is a good point, and I forgot to mention that.  Yes, I have checked the boot order and it is set to boot cd first.  I also burned the CD and then tried to boot with the Virtualbox off the cd and it says the media is not bootable.  I forgot to add those details.  I haven't tried booting the CD in another machine (besides the virtual machine because I know this does boot off CD as I just recently installed Ubuntu.

Shane

---

### Post by zvacet on 2007-04-17
It have to be iso image not data.If you burned iso image and still no luck try to burn it on lower possible speed.That is all I can think of right now.
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by taurus on 2007-04-17
If you view the contend of the CD whether with Windows or another Linux machine, you should see a bunch of files and directories, not just one big file that you downloaded.  If you see a one large file on the CD, then you just copied it from a harddrive over to a CD.  Therefore, you need to burn that .iso file as an image file, not a data file or just copied it over to a CD.

---

### Post by shane2peru on 2007-04-17
> **taurus said:**
> If you view the contend of the CD whether with Windows or another Linux machine, you should see a bunch of files and directories, not just one big file that you downloaded.  If you see a one large file on the CD, then you just copied it from a harddrive over to a CD.  Therefore, you need to burn that .iso file as an image file, not a data file or just copied it over to a CD.
No, I can see the all the files.  It has folders with the linux files for install.  Is there any possibility that the CD Burner is not configured right?  or is it Programing?  Thanks for the help.  I'm burning it as an image, like I have done in the past on my laptop, and the weird thing is that it is naming the CD with a date system.  

Shane

---

### Post by shane2peru on 2007-04-18
Never mind.  I just figured out that my LG DVD burner cannot burn to Memorex media!  I tried an Imation disk, and it burned fine.  Disk booted and everything.  I thought the incompatibility problems with media and drives was a thing of the past, I guess not.  Thanks for the help.  I knew it had to be something simple like that.

Shane

---

