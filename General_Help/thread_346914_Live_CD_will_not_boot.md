---
title: "Live CD will not boot"
date: 2007-01-26
forum: General Help
---

### Post by bigal1985 on 2007-01-26
I have a live cd of Ubuntu 6.10.  It will not boot on my desktop computer.  I have successfully booted this CD on my g/f's new desktop that I built and my really old laptop (PIII 800mhz).  My desktop is:

MSI K8N nForce4
AMD A64 3200
WD 80gb SATA HDD
MSI Rx800 pci-express
corsair 2 x 512mb DDR

The spash screen comes up, the orange block bounces around, then the meter fills up with orange.  Right when the meter gets to full, the "ubuntu" turns green and a green line appears on the screen.  From there, the systems freezes, the cd-rom stops spinning and nothing else happens.  Like I mentioned before, this same disk booted wonderfully on a new computer and my old laptop.  Any help would be greatly appreciated.

---

### Post by lyceum on 2007-01-26
Looking at your stats and the fact that the disk worked with other computers, I have no idea, but to guess, you could run the disk check before boot. Also, if you are tring to install you could use the alternate CD, but you really shouldn't need to. :confused:

---

### Post by majoridiot on 2007-01-26
you might also try burning the cd again at a slower speed.  i have had many instances of cds
booting on one comp and not another, due to idiosyncarcies of cd drives.  the general rule
of thumb that i use for boot cds is to burn at half the rated speed of the drive- e.g. burn @
24x for 48x/52x rated drive (assuming the media can handle the speed too)... it seemed to 
eliminate the problem for me.

you might also try doing a ram test from the boot screen as well to ensure there isn't something
lurking that the installer doesn't like.

---

### Post by Steve S. on 2007-01-26
Well, I've only got to play with older drives, but when I come accross that issue, it was either the burn speed of the cd or the hard drive was bad...most of the time.  Occasionally the cd player was bad.

But, like I said, the stuff I usually deal with is junk and I'm just looking for a diamond in the rough...

---

### Post by bigal1985 on 2007-01-26
Well, I've tried reburning the CD at a lower speed, running with the 'noapic' option, and unplugging the SATA hard drive.....still nothing.  I am wanting to try a different video card.  I have been having trouble with my video lately in windows, I'm not sure if its directx or the card.  Again, it works on yet another computer, a 1.4ghz P4.  I think I might try to install using the alternate CD when I round up another hard drive.

---

### Post by igknighted on 2007-01-27
Your problem is the graphics card (ATI x800).  I have the same card and the live CD does not detect it well and use the proper video drivers.  Your best bet is to install via the alternate CD then install the drivers for your x800 once the system is installed.

---

### Post by terrapin28 on 2007-01-28
I have experienced the _exact_ same problem when installing from the 6.10 disc. As far as I can tell there is a problem with the x server ati drivers and the x800 video card.  I know I have had success in the past by simply using the backwards compatible vesa drivers to get up and running. Unfortunately, I don't know if there is a way to do this from the 6.10 disc. Maybe there is a switch that can be thrown in at boot time? I know that by simply switching the boot option to safe graphics seems to crash the system as well.

You might want to look at this post
[http://www.ubuntuforums.org/showthread.php?t=347216&highlight=ati+x800](http://www.ubuntuforums.org/showthread.php?t=347216&highlight=ati+x800)

---

### Post by bigal1985 on 2007-01-28
Good replies, I swapped out the x800 for the x300 that I bought for my g/f's computer....booted up like a charm.  Also, that fixed my gaming problem in Windows.  The graphics weren't great but at least they weren't going crazy.   So it looks like I will be getting a new video card.  Thanks for the help!!!

---

