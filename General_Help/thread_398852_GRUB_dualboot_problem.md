---
title: "GRUB dualboot problem"
date: 2007-04-01
forum: General Help
---

### Post by xubu_caapn on 2007-04-01
hey everyone,
i recently installed ubuntu 6.10 on an external hdd on my father's windows computer, which is on the main hdd. it installed grub on the external hdd, so i have to have it on when booting into windows, but i can turn it off once it's booted. i don't know if this caused the problem, but my father complained that windows is crawling, so i installed spybot and kaspersky, removed the little adware there was, defragmented the disk and all that stuff, but it's still as slow as ever. i'm usually not on this computer so i don't know if the ubuntu installation caused the problem or if they just coincided, but is grub capable of slowing down this windows desktop so drastically? is it a problem that i have it on the external hdd? do i need grub once the os is loaded? ubuntu runs smoothly and i haven't had any problems with slow down with it, but in windows everything is just so sluggish. (this is a brand new computer by the way, athlon 64 3500+, gig of ram...). so any ideas? thanks for the help!

---

### Post by xubu_caapn on 2007-04-01
bump..
it wouldn't be so urgent but this isn't my computer here, heh
any help appreciated

---

### Post by Cappy on 2007-04-01
If grub is installed on the external hdd you should be able to go into BIOS and change the boot order to boot from the internal hard drive instead. At least then you can find out if it's related to GRUB or not.

---

### Post by xubu_caapn on 2007-04-03
alright, i'm going to just remove linux and do the fixmbr thing...
are there any concerns using this method to restore the bootloader? is there any risk of wiping the winxp harddrive? it's tax season, so i don't think my dad would like that (of course i would back everything up before hand, but in any case...). 

thanks for the help

---

### Post by confused57 on 2007-04-03
> **xubu_caapn said:**
> alright, i'm going to just remove linux and do the fixmbr thing...
are there any concerns using this method to restore the bootloader? is there any risk of wiping the winxp harddrive? it's tax season, so i don't think my dad would like that (of course i would back everything up before hand, but in any case...). 

thanks for the help

I believe you actually installed grub to the internal hard drive, since you must have the external hard drive connected to boot Ubuntu.  The FIXMBR should restore the internal drive mbr so that Window's will boot without the external drive connected.  You have to have the Window's install cd(not a recovery cd) to do so:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
  
You can also use the Super Grub Disk to repair your mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If your dad's computer is capable of booting first to the USB external hard drive, you might want to use the live cd to install grub to the external drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This way, the computer will boot into Windows with the external drive disconnected and you can boot to the external drive by selecting it to boot before the internal hard drive.  If you want to do this, when you boot first to the external hd and get a grub menu, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), press "b" to boot.

---

