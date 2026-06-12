---
title: "Black Screen on most boots after installing then uninstalling fglrx. ATI/AMD Drivers."
date: 2015-08-04
forum: General Help
---

### Post by CavemanNinja on 2015-08-04
Hi Ubuntu Forums, I've never had to ask for help to fix something before but I've mucked things up royally this time and fear I'm out of my depth. 

I'm running 15.04 with an HD6870 I had the open source drivers installed everything working fine. Steam required installing the proprietary drivers.

I downloaded and installed the drivers from the AMD website following the instructions in their pdf which was basically download the deb packages and install them with dpkg then run 

```
sudo amdconfig -initial
```

I went to back up by /etc/X11/xorg.conf file before installing the proprietary drivers and I did not find one. i.e. I did not have an xorg.conf file to start with but everything was working fine. 

After installing the AMD driver the PC boots okay but one of my screens won't work, I read I need an active display port adapter to make it work, I don't have one so decide it's not worth it for steam decide to remove the proprietary drivers with

sudo apt-get remove --purge fglrx*

reboot and after the grub selection menu I get a black screen then my monitors turn off, but my computer is still on. 

I booted into recovery root shell and tried reinstalling the radeon drivers, 

```
apt-get install xserver-xorg-core xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
dpkg-reconfigure xserver-xorg

```
and removed all xorg.conf files from /etc/X11 

and it didn't help still the same booting to black screen although 1/10 times it will actually load graphics driver and everything works properly. 

I found it does work when I add nomodesetting to grub but that loads with the vesa driver and doesn't set my screen resolutions correctly or turn on all the monitors. 

Things I have tried:

I kept seeing the acpi probe failed error during startup so I added acpi=off to grub linux command line (no difference).
tried radeon.modesetting=1 (no difference)
nomodesetting (loads but resolution is messed up, can't detect displays in settings)
Reset BIOS Settings (loaded okay first few times then back to black screen like before)
upgraded from 3.19 kernel to the 4.1.0-rc2 (no difference)

There's something wrong with my video driver, please help me troubleshoot and find where it is!

---

### Post by sp40140 on 2015-08-04
You can try this: remove ~/.xauthority. So, boot into recovery shell and remove this folder (or rename if you prefer). It will be re-created when you reboot. This has worked for me in the past when dealing with AMD/ATI drivers (HD7770).
Heads-up: You should avoid installing vid drivers manaually. This will cause more problems than fixes. Install prop drivers from "additional drivers" section in update settings.

Cheers

---

### Post by CavemanNinja on 2015-08-04
rename .Xauthority _.Xauthority in recovery and tried to reboot, it didn't work. Thanks for the suggestion though. 

I wish I had done it through additional drivers but alas when I reinstalled the open source drivers I didn't realize that I could get a successful boot if I just kept restarting over and over :(

I tried renaming the whole /etc/X11 directory _X11 and booting, and instead of failing it boots into graphics failsafe mode, which is expected, but trying to reconfigure graphics option through failsafe nothing happens. Also dpkg-reconfigure xserver-xorg which I though would regenrate a xorg.conf for me seems to do nothing :/

Really strange that sometimes it works perfectly, that's really confusing to me. Shouldn't it either work or not!

---

### Post by sp40140 on 2015-08-05
You mentioned that you upgraded to kernel 4.1.0! That has not been issued by Ubuntu in standard update. Are you still running it or did you rollback to 3.19?
If you are running 4.1.0, I would suggest you go back to 3.19.25.

---

### Post by pulpo692 on 2015-08-05
The fglrx-black-screen-problem is also happening to me with a standard ubuntu gnome installation (vivid). That's annoying because the free ati driver always cut off some screen, I need the catalyst overscan configration option (overscan) for seeing the whole screen.

---

### Post by CavemanNinja on 2015-08-05
I'll try rolling back the kernel and report back. 

The reason I upgraded was I had a problem with my laptop after installing 15.04 where the trackpad wasn't being recognized properly and upgrading to 4.0 solved it. I've read 4.0 has some better hardware handling so I guess I was hoping it would be a magic bullet for my graphics drivers problems as well. Sigh. 

@pulpo692 is the overscan option back? AFAIK the last time I tried the catalyst driver they had removed the overscan option, that was a couple years ago though. It's back on Windows but it might have never been taken out of that version, I remember when they took it out I had to go to an earlier version of the catalyst driver because my old monitor would have black bars around all edges. 

I would have reinstalled by now but the fact that it works 1/10 times I try to boot gives me hope that I can fix the problem. I'm using the machine currently and everything is working fine. Except I did have animations turned off in gnome and now they are back... don't know if that will give anyone out there a clue as to what has gone wrong!

If I could get a log of what happens when it works correctly and compare that to what happens when it crashes, that might give some insight into what the problem is. Any ideas where I could look?

---

### Post by pulpo692 on 2015-08-09
Fglrx seems to be updated an is working now here. Problem solved. Ubuntu Gnome 15.04.

---

