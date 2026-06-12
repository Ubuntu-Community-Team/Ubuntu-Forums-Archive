---
title: "Cupsys Upgrade, Newbie Screwup"
date: 2007-12-06
forum: General Help
---

### Post by arwilson529 on 2007-12-06
I am exceedingly new to Linux and Ubuntu - for the past two months I've been trying to get a distro of Linux to work on my computer, paid too much money for Xandros that didn't work and their tech support was worthless.  Ubuntu seems to be the only thing that works for me.  I've enjoyed it a lot thus far, but have yet to get a full day's use out of it!

I just recently got the 32-bit version to work, and began to upgrade the system, install new software, all kinds of stuff.  I let the upgrade process run over night.  When I woke up I noticed it had locked up on the install process, where it began "Configuring Cupsys."  The keyboard wouldn't work but the mouse would.  I couldn't think of anything else to do but do a hard reboot.  When GDM loaded and I plugged in my user/PW, nothing loaded.  It just stayed on the off-white screen.  My cursor showed up but nothing else.  

So I loaded up in Recovery mode, thinking maybe its a diagnostic thing.  Recovery mode stopped at "Kernel panic - not syncing.  Creation of kmalloc slab kmallo_dma-512 size=512 failed."  Looking through the forum it seems a lot of people had issues with Cupsys but I found nothing in relation to the kmalloc thing.  Maybe two problems?  I dunno.  

I figured maybe hibernation mode could have goofed up the install?  I dunno, but I had a few problems with that when I tried the 64-bit version.  It would come out of sleep and a big black box would be in the middle, but using the monitor's buttons to refresh it and it was fixed.  

I just learned how to get into the terminal using key commands and what the fsck command does, so that will be my next step, but I'd like to get any recommendations now before I get home from work and actually get to experiment with this.  So far its been a great OS.  Outside of this, having to figure out why I couldn't install or upgrade stuff (repositories turned off, lol), and my Abit Airpace PCI-E wireless card not working even through ndiswrapper, no complaints!  Already better than Xandros, MEPIS, and others - at least this one installed!!  Thanks

---

### Post by barney_1 on 2007-12-06
Ok, lots to deal with here.

First off, I would stick with the 32-bit version unless you have a very good reason that you need the 64-bit version.  In the past (this may be changing with the development cycles) a lot of applications had trouble with the 64-bit version.

Be careful with fsck.  It's a great tool but make sure you know what each command your are typing does before you do it.

Personally, my very first step would be to get to a command prompt (using recovery mode if necessary) and make sure you have your packages fully upgraded:
```
sudo apt-get update
sudo apt-get upgrade
```

If you get any complaints in that process that you can't resolve, post them back here.

---

### Post by arwilson529 on 2007-12-06
Well, I think I at least fixed the problem temporarily.  I did more research on the forum and fixed X, using the following:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```
Then I selected my resolution and.......
```
sudo dpkg --configure -a
```

It ran through a bunch of stuff, farted up on my Network Manager (hung there for about 4 minutes), then finished whatever it was doing.  It again locked up (keyboard wouldn't work at least), so I hard rebooted.  Then ubuntu was fine.  :: shrugs::  

Going to check those packages now.  I would have done that first but my wireless internet was difficult to set up in the terminal, lol

---

