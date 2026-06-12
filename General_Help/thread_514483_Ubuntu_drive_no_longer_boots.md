---
title: "Ubuntu drive no longer boots"
date: 2007-07-31
forum: General Help
---

### Post by DarkGob on 2007-07-31
I've had the following setup working fine since I started using Ubuntu, a few months ago -- two hard drives, Ubuntu and WinXP, set as master and slave respectively (both jumpers on cable select).  Earlier today I did some fiddling around with the drives that involved trying to get my Ubuntu drive as a master and another drive (Win2000) as a slave, so I could get some data off the Win2000 drive.  At least, I think that was the setup, I don't really remember, but the point is there was much switching of cables and jumper settings and all that stuff.  I ended up getting the files off the Win2000 drive with the Ubuntu Live CD and a Zip drive, so since I no longer needed to bother with the Win2000 drive I attempted to go back to my original setup.  Only problem is, now my Ubuntu drive won't boot at all (the drive is detected, though).  Even when the Ubuntu drive is the only drive in there, it just won't boot.  It just loads into some Boot Agent that results in an error message asking for a system disk.

Looking through a few other threads, it looks like I may have screwed something up with the way Ubuntu assigns drives.  Reinstall is a very very very very very very very very very very very very very very VERY last option for me -- WinXP won't identify my Ubuntu drive when I try to set it as slave, nor will the Live CD, so I have no way to get my data off the drive.

EDIT: Okay, it seems the drive is actually NOT being detected anymore period, which goes a long way towards explaining why it doesn't appear when I use the Live CD (it was never visible in WinXP though).    I tried leaving the jumper set to master, I tried putting it on cable select, but neither of those work.

When I try to use the Live CD to boot from my Ubuntu drive as my master (and only) drive, I get the following error message:

isolinux: Disk error 01, AX=0201, drive 80

Please help me!  I don't think I can take another complete OS reinstall (that's what drove me to Linux to begin with).

---

### Post by nitro_n2o on 2007-07-31
check out this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) it saved me once :)

---

### Post by DarkGob on 2007-07-31
> **nitro_n2o said:**
> check out this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) it saved me once :)

After the second step I get Error 15: File not found, which I suppose makes sense if the drive isn't even being detected by the motherboard.

---

### Post by DarkGob on 2007-08-01
SPOILER ALERT!  It was the drive cable.

---

