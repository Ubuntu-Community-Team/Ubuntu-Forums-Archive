---
title: "Problem installing Build-essentail Linux-headers from CD"
date: 2008-03-27
forum: General Help
---

### Post by DieselSnorter on 2008-03-27
I'm trying to run the following 
sudo apt-cdrom add 
and getting an error that I can't mount the CDrom

This is a cd I just downloaded as I installed Ubuntu back with Edgy I think and have upgraded from there.  

I don't have an internet connection for that PC (that's what i'm trying to fix) so without moving that PC to another room, I'd like to get it working like this.

---

### Post by cmnorton on 2008-03-27
This sounds like a mismatch between your old version of Ubuntu and the CD you downloaded, though the error message sounds funny.

I'd move the PC to the other room, and use the internet, or go with wireless.

Can you mount the CD? If you insert an Ubuntu CD, usually you'll see an icon on your desktop indicating the CD has mounted.

---

### Post by DieselSnorter on 2008-03-27
The CD loads and pops right up in an explorer type window.  If I boot with it in, it gives me the option to install. 

I'm trying to get this working so I can follow the steps here [http://ubuntuforums.org/showthread.php?t=400236&highlight=wireless]("http://ubuntuforums.org/showthread.php?t=400236&highlight=wireless")
and get my wireless working. 

If it's not an easy fix, I'll drag the PC into the other room.

---

### Post by cmnorton on 2008-03-27
Please google this

sudo apt-cdrom add

I just saw so much stuff related to this, it would not be worth posting all the links here. This included references to the media not mounting.

---

### Post by DieselSnorter on 2008-03-27
so, if I run sudo apt-cdrom -m add I get the following
Using CD-ROM mount point /cdrom/
identifying {22c85blahblahblahblah]
scanning disc for index files
found 0 package indexses, 0 source indexes, 0 translation indexes and 0 signatures
E:  Unable to locate any package files, perhaps this is not a debian disc.

I downloaded it from releases.ubuntu.com.

could I have downloaded the wrong CD?

---

### Post by cmnorton on 2008-03-28
This sounds like part of the disk did not get either downloaded completely or properly and that indeed your disk is invalid.

---

