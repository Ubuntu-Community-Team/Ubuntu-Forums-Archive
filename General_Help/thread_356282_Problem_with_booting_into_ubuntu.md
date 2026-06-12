---
title: "Problem with booting into ubuntu"
date: 2007-02-08
forum: General Help
---

### Post by Bluey on 2007-02-08
Hey guys. I recently installed ubuntu 6.06 LTS - the Dapper Drake, making the switch to linux instead of vista.. Anyway, Im having trouble booting up. I start by turning on the computer, it gets to the boot screen and I choose the normal mode for ubuntu. It comes up with the nice graphical loading screen which it loads up to the Enterprize Sound Management System which at that point it goes into a non-graphical mode and starts outputing what looks to be hard drive errors. What it seems to do is output five of these errors

> Translated ATA stat/err 0x51/40 to SCSI sk/a sc/asc 0x3 blah blah... didnt copy the rest..


And then after every five of those errors it outputs one of these
> Buffer I/O error on device dm-4, logical block 31...

This loops through that process for about four minutes until it stops and loads everything else and goes into ubuntu.

What do these erorrs mean and what would be the solution? What is this Enterprize Sound Management System?

If it helps, the default sound is ALi M5455, I havnt updated the drivers for the motherboard. I did have a previous 64bit version of ubuntu on this computer and never got these errors. I have also mounted a sata NTFS partion.

Thanks, Bluey.

---

### Post by robcarr2 on 2007-02-15
Hmm, I never saw any errors like that when using Dapper, all I can suggest is either trying a fresh or install, or trying out Edgy. I am running Edgy at the moment and it has been fine so far (with the exception of getting my ATI driver to work!)

If you do decide to try out Edgy I suggest using this program to install your nVidia or ATi drivers:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Thats if you have an ATi or nVidia video card of course :)

---

