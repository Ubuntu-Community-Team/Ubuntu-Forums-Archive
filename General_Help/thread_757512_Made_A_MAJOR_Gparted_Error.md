---
title: "Made A MAJOR Gparted Error"
date: 2008-04-17
forum: General Help
---

### Post by Puptentacle on 2008-04-17
In an effort to load Linux on a thumb drive, I downloaded Gnome Partition Editor. Opening it I discovered five GB of unpartitioned space on my HD. "Well", says I "I'd really like to have that where I can use it." So, I partitioned it ext3, and went to rename it. Somehow I managed to rename or unallocate the ENTIRE DRIVE! I immediately tried to undo last operation but to no avail.  Now, I'm getting Error 22 from Grub, the live CD won't read the HD, and the Gparted live CD shows the drive unallocated and give me no options other than 

The world isn't going to end if I have to reinstall BUT there is information on one of the partitions that I'd seriously like to have back, not to mention several months worth of programs and customization. 

Is there any way to get this back? 

Since there's never too much information, here's the specs:
HP Pavillion DV2500 laptop
Centrino Duo 1.5ghz
2gb ram

---

### Post by nicedude on 2008-04-17
Use "testdisk" to recover data from your lost partition, its been covered before so below is the link to a previous guys problem identical to yours. You have to read to almost the bottom of the posts on this page though as someone first trys to suggest fixing with parted   (which you could probably try first but if it doesn't work than this will at least get back your data) go down the page to where a member named "slick1a" lists the steps for how to use it, hope this helps you get your data recovered.

[http://ubuntuforums.org/showthread.php?t=244676](http://ubuntuforums.org/showthread.php?t=244676)   

If your ubuntu live disk doesn't have testdisk on it you can get a rescue disk with it here

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

Goodluck

---

### Post by Puptentacle on 2008-04-17
I figured I'd killed the install. Another lesson learned. Thanks a lot!

---

### Post by Puptentacle on 2008-04-17
MY INSTALL! IT LIVES! 

Thanks to you for pointing that thread out (I searched several ways and couldn't find it) and thanks to Slick1A on the other thread. TestDisk did the job. Nothing lost!

---

