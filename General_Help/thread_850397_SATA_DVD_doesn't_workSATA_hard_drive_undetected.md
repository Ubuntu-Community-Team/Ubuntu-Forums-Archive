---
title: "SATA DVD doesn't work/SATA hard drive undetected"
date: 2008-07-05
forum: General Help
---

### Post by Cogman on 2008-07-05
I have 2 hard drives right now a 160gb WD sata, and an 80 gb WD sata as well as 1 sata DVD-burner.

I have an Asus P5Q-E with a quad core. I was able to install the ubuntu by plugging in my existing IDE DVD but am unable to use the sata DVD. I know the sata dvd works because it will boot up to the ubuntu start menu (it won't completely boot up ubuntu though. In text mode it says it can't find the CD-ROM drivers.)

The other problem I have is that I can't see my 80 GB hard-drive. I want to transfer some data off of it but obviously can since I can't see it. Any tips/has anyone else gotten a SATA dvd-burner to work on their version of ubuntu (it is a Samsung burner btw)

I hope I've been clean. Im not scared to use the console or vim btw so any technical hoops won't scare me. (I am updating my distro right now so maybe the problem will disappear, but I doubt it)

---

### Post by logos34 on 2008-07-05
Does linux detect the two drive in question at all?

**sudo lshw -C disk**

Also, check

**sudo nano /etc/fstab**
(is there a line '/dev/scd1...' for the second cd/dvd burner?)

[B]ls -l /media

ls -l /dev | grep dvd

[/B] check to make sure the Bios is detecting the 80 gb correctly

---

### Post by Terc on 2008-08-11
I'm having the same issue with my P5Q-E SATA drive not detected, the same drive works under p965 chipset with ICH8 (P5B-Deluxe).

---

### Post by MushNut on 2009-04-14
I am having the same problem on my ICH7 based mobo.  I would appreciate any help.  My SATA HDD is working just fine but my DVDRW drive is recognized but won't mount.  Thank you for your help.

---

### Post by pepsifx357 on 2010-03-18
Did anyone find a solution to this problem?  I've got an HP lightscribe external DVD Burner that I removed the housing on.  Turns out it was Slimline-SATA.  I hooked it up.  The light comes on it opens, it sounds like its reading the disk, but ubuntu doesn't detect the disk.

---

