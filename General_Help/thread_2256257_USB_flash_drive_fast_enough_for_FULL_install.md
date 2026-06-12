---
title: "USB flash drive fast enough for FULL install?"
date: 2014-12-11
forum: General Help
---

### Post by thatguymark on 2014-12-11
I'm thinking of doing this instead of live USB with persistent storage, my understanding is it would allow for upgrading the kernel and everything you can do with a normal install. My question is how to go about determining if a given drive will be fast enough. I understand wear leveling is an issue and no doubt there are a number of USB 3.0 models that are pretty fast now, but I'd like to know what particular specs to look for, most likely in a review and not in the published mfg specs like 1k and such. I guess I could have gone to a hardware forum elsewhere but figured since I plan to use Ubuntu anyway I might as well ask here, but could not find a hardware forum other than the one designated for troubleshooting hardware that's not working.

---

### Post by C.S.Cameron on 2014-12-11
See Sudodus' post in this thread:

[http://ubuntuforums.org/showthread.php?t=2256107](http://ubuntuforums.org/showthread.php?t=2256107)
Good links

I have only heard of one report of a pendrive failing from running Ubuntu and that was a cheapo drive and overuse may not have been the cause.

---

### Post by oldfred on 2014-12-11
I have a full install on a flash drive, but it is more for a backup way to boot my laptop.

The install is very slow, for me I can install from an ISO on a hard drive to my SSD in 10 minutes, but to flash drive it is over an hour.

Since writes are so slow you want to minimize those even at the expense of reliability. 
I use ext4 as it supposed is better but turn off journal. If partition is smaller then journal only adds some savings in fsck time, but you may lose the recovery capability in some cases.
 sudo tune2fs -O ^has_journal /dev/sdb1


I also add to fstab noatime, so it is not writing update times. That can be an issue with a very few apps like mutt, but I have not had any issues.

Any new partition tools should set partitions on good alignment.

If you have a fair amount of RAM - 4GB or more,  RAM caches most of your applications once loaded. So if not loading many applications at once or reusing the same applications that may already be in RAM make system seem just as fast as a hard drive. In both cases RAM is reading program, not from drive.

---

### Post by HermanAB on 2014-12-11
Howdy,

It will work once installed, since operation is mostly reading and very little writing.

However, a speed number 6, SD card may be a better idea.

---

### Post by mc4man on 2014-12-11
How well it works out depends on which flash drive & what you do.
Here have tried - 
sandisk ultra - not that good
sandisk extreme - ok for basic use, multitasking that involves writing is slow

I 've also tried (& currently using)  - angelbird ssd2go
In this case worked great for about 6 months, then either somethings gone bad on the drive or I screwed it up by doing a full format for some unknown & stupid  reason. Now it's just ok but writes slow compared to before
One issue with any usb 3 flash or ssd drive is garbage collection is up to the drive, trim & secure-erase aren't usable via usb.

---

### Post by thatguymark on 2014-12-12
Thanks everyone! Bookmarking this one..

---

