---
title: "install issues"
date: 2007-02-16
forum: General Help
---

### Post by paitken on 2007-02-16
I have tried 6.10 and 7.0 releases of Ubuntu.  Below are my results.

6.10:
I press enter, with the CD's default settings.  Then, the next screen loads.  It is a bit distorted and has no color.  I wait about 5-10 minutes, and a command line-like interface comes up.  Gives me errors saying something along the lines of "block i/o error on device /dev/hda"...And this just continuously happens.

7.0:
I start the CD with the default settings.  Then the next screen loads, it's in color and it looks fine.  However, after it finishes loading, it takes me to a screen where I can see the mouse move, but it's just a block of noise (dots) and so is the bottom half of the screen and the top half is just black.

I have a 19" lcd monitor (q19wb) - [http://www.viewsonic.com/products/desktopdisplays/lcddisplays/optiquest/q19wb/#specs](http://www.viewsonic.com/products/desktopdisplays/lcddisplays/optiquest/q19wb/#specs)

It is hooked up via a VGA cable, because it has no DVI.

Hardware:
Motherboard - MSI K9N SLI PLATINUM (Nforce 570 chipset) - [http://www.newegg.com/Product/Product.asp?Item=N82E16813130048](http://www.newegg.com/Product/Product.asp?Item=N82E16813130048)

I have a software based RAID 0 running windows on 2 300gb hitachi drives, and I also have 1 80gb SATA drive installed -- which currently has SLAMD64.  I have a DVD-RW Drive, 2gb ram..and a nVidia 6600LE (I think)

I have used linux on this machine/drive before, so I know the drive is not bad.  I tried googling, irc, the forums, etc.  I need some help, thank you.

---

### Post by paitken on 2007-02-16
Okay, I got it working with Edgy.  However, now I am having issues with GRUB.

I have a software RAID that I run Windows XP on.  Ubuntu reads these two drives as:
/dev/sda
/dev/sdb

I also have an 80GB HD, which I am trying to install Ubuntu on. (/dev/sdc).  I have two partitions.  /dev/sdc1 and /dev/sdc2

GRUB installed on HD0 (Not sure if that's SDA or not).  

After installing, I reboot and I get
GRUB Loading State1.5
Error 21...

And the screen stays black.  Nothing happens.

I'm not sure where to go from there.

---

