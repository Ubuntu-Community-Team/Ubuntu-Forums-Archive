---
title: "cant manage to keep ubuntu from losing data"
date: 2015-01-26
forum: General Help
---

### Post by dhruv3 on 2015-01-26
Ubuntu keeps losing boot up files when it doesn't get turned off properly and its very annoying is there a fix? Hard drive is intact and I'm not sure if there are any errors

---

### Post by TheFu on 2015-01-26
Considering that the /boot area is read-only unless a new kernel is being installed, there are a few things to check
* CMOS battery - this retains boot settings like which disk to boot from.
* bad sata cable
* bad sata controller
* failing disk sectors.

Swap each out one at a time and test until you've determined which is the issue.

---

### Post by efflandt on 2015-01-27
Why is not being turned off properly? I have been running Linux for about 20 years (before I had Win95) and I don't remember every having a problem with lost data if something hung and I had to do a hard shutdown, or power failure, although, I normally have my computer on a UPS and have not been in the middle of trying to save a file during those conditions. I have had drives fail gradually, most recently over a year ago. One sign of drive problems is if you suddenly cannot save a file because the system automatically remounted your drive read-only. In my case it was when sectors started going bad in my Linux partition at the far end of a 3 year old drive. I was able to patch it up a few times with fsck options to lock out badblocks from a small Ubuntu installation on another drive, but eventually replaced the failing drive. Yet I have a warranty replacement drive on an old Celeron 333 MHz PC in my basement that has been running an obsolete version of SuSE (8.2) for over 10 years 24/7 including a 5 year stretch from July 2006 to July 2011 without rebooting between prolonged power failures. But many years ago I had one drive that started getting bad sectors when less than a month old. So you never know if a drive is going to last indefinitely or suddenly dump on you.

Athough, one time while running SETI@home years ago (which used 100% of available CPU) I suddenly got an error that it could not write to its logs, apparently because its drives were overheating when I checked their temperatures. I found that the inlet fan was totally packed with lint sucked up from the carpet. Once I cleaned that out and it had cooled down, it was none the worse for wear and everything worked fine.

Drives normally reserve some space to automatically transparently remap in place of bad sectors regardless of OS. So if you actually start noticing bad sectors (or your drive remounting read-only), all the error sites may be used up and it can only get worse.

---

### Post by The Cog on 2015-01-27
I can't help with why it won't shut down properly, but I will suggest that you change to a different filesystem until you get the shutdown fixed. In my experience, ext4 is very likely to lose huge quantities of files and folders if it doesn't shut down cleanly. I have found that jfs and btrfs seem quite resilient in this respect. I haven't tried other filesystems.

---

### Post by Bucky Ball on 2015-01-27
I'd be looking at why it doesn't turn off properly. Perhaps follow TheFu's advice if it is not the user but the machine creating the unexpected shutdown.

---

