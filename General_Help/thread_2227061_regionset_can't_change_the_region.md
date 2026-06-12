---
title: "regionset: can't change the region"
date: 2014-05-30
forum: General Help
---

### Post by fabagruen on 2014-05-30
Hello there, maybe u can help me:
I can t play any bought DVDs on my computer. Installing libdvdread4 didn t help. I downloaded regionset and want to change the region to region 2. but the output looks like that:
regionset /media
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "/media"!
Please ensure there is a readable CD or DVD in the drive.

any ideas?

---

### Post by slickymaster on 2014-05-30
Hi fabagruen, welcome to the forums.

Ubuntu can’t play DVDs out of the box for a whole tangle of legal reasons. Besides libdvdread4, which you need to read the DVD, you probably will need **libdvdcss2** to recognize the DVD and **libdvdnav4 **to navigate the DVD.

---

### Post by mcduck on 2014-05-30
You need to point regionset to the DVD *device*, which more than likely isn't /media. Try something like /dev/dvd instead. Also regionset needs root permissions, so you should run it with sudo.

---

### Post by mc4man on 2014-05-30
As mentioned you need to specify drive & have any disk in the drive to run regionset,  I'd use /dev/sr0 or /dev/sr1 as /dev/dvd no longer exists in current Ubuntu. Using sudo is not needed.
Ex.
```
regionset /dev/sr0
```
(you can ck. with an lshw command which your drive is

In linux, when using unlicensed open source players like vlc, ect.,  having a region code set  is generally  irrelevant except when - 
The dvd has  RCE (region coding enhanced), in that case a region should be set once on your drive, though which region doesn't really matter, just set to whichever you have the most dvds.
(in other words you can play dvds from any region, not just the one the drive is set to.

The other exception is if the drive is a matshita drive,  then you must  set a region & you'll only  be able to play dvds from that set region. If there is a region mismatch then matshita drives will not allow access to encrypted sectors.

So if adding libdvdcss2 doesn't resolve -  first find the drive & then use regionset appropriately

```
sudo lshw -C disk
```
Look under the *-cdrom section for device link. (/dev/sr0 or /dev/sr1), & ck. on whether it's a matshita drive

---

### Post by fabagruen on 2014-05-31
Hey, thanks. 
I just had to specify the dvd devise correctly with /dev/sr0, then everything worked out. Thanks a lot. :)

---

