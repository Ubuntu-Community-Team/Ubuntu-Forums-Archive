---
title: "Needing a Fresh Start on a difficult PC"
date: 2007-08-18
forum: General Help
---

### Post by Deagreay on 2007-08-18
Okay, I've screwed around with the Ubuntu grub and my partition of Windows, when I boot normally I get a disk read error, I've set cd-rom drive to boot first so I do have access to that, is there a way I can just wipe my hard drive and install Xp Professional? When I try to boot windows from the Super GRUB it just gets stuck in the boot process, and it will sit there for hours.

---

### Post by Scunizi on 2007-08-18
Instead of using SuperGrub you might try the instructions of redoing grub listed at [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by 1/0 on 2007-08-18
If you've only messed with GRUB you should be able to set GRUB to boot properly but if you've partitioned or formated your drive/partition then you're more or less fsck:ed.

To wipe your HDD just use fdisk or do it from the XP install cd. The thing is that MS Windows XP doesn't use the MBR so you need to reset it in Windows/DOS by:

```
format  /MBR
```

In Linux you can do this:

```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```

But be aware! This wipes you HDD clean so BACKUP!

---

### Post by Deagreay on 2007-08-18
> **1/0 said:**
> 

In Linux you can do this:

```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```

But be aware! This wipes you HDD clean so BACKUP!

I try that but it says " '/dev/hda' " denied

---

### Post by 1/0 on 2007-08-18
I forgot to write that you need root privileges to do that. Just add sudo in front and it will work, but remember this wipes your hard drive.

---

### Post by Deagreay on 2007-08-18
okay this post makes a jerk out of me, but I cannot bear losing my Windows data.  And the fact that I just learned that the windows professional disc that was never used is scratched up beyond repair... I need to figure out how to access Windows Xp Home, I've tried using grub and super grub but they both get stuck in the process of booting, I haven't been able to set MBR, or fix boot or anything! Help!

---

