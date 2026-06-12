---
title: "Desktop effects with ATI Radeon Mobility M6 LY"
date: 2008-04-26
forum: General Help
---

### Post by nami on 2008-04-26
I was able to get desktop effects to work on my laptop in Ubuntu 7.10 using the following amendments to xorg.conf:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"        "true"
	Option		"AGPMode" "4"
	Option		"AGPSize" "64" # default: 8
	Option		"RingSize" "8"
	Option		"BufferSize" "2"
	Option		"EnablePageFlip" "True"
	Option		"EnableDepthMoves" "True"
	Option		"RenderAccel" "true"
EndSection

But this does not seem to work with Ubuntu 8.04.  Can someone please help?

---

### Post by Zorael on 2008-04-26
Some ati laptop cards have been blacklisted. What is the terminal output of compiz --replace?
```
$ compiz --replace &
```
If it says 'found ati laptop, aborting' or something to that extent, try appending 'SKIP_CHECKS=yes' to the command.
```
$ SKIP_CHECKS=yes compiz --replace &
```

If that works, there is a more permanent fix. See [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875).

---

### Post by nami on 2008-04-26
it says what xgl was not found or something along those lines.

---

### Post by Zorael on 2008-04-26
Okay.

Reading more carefully, I see that you seem to be running the open, non-GL accelerated ati driver.
```
Driver "ati"
```

Have you tried it with the proprietary one? You can enable it in the Restricted Drivers app, or by installing it through envyNG from the repositories.

As for Xgl not being found, you don't want it; it will use software rendering and things will be mighty, mighty slow. :>

If you want to try it out, just install the xserver-xgl package.

---

### Post by nami on 2008-04-26
Where is the restricted drivers app in 8.04?  The closest thing I can find for that is system > administration > hardware drivers.  And in that app it says: no proprietary drivers are in use on this system.

---

### Post by Zorael on 2008-04-26
Oh, right, KDE. My bad.

Try running **kdesudo jockey-kde** from a run box (Alt+F2) or a terminal. If that doesn't work, things are complicated.

Basically, you want to change to the fglrx drivers and enable aiglx support. If that doesn't ring a bell, basically it boils down to adding a whole bunch of options to xorg.conf.

You can either manually do this by following a how-to guide (such as [http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)), or you could have envyNG do it for you. It's in the repositories now, package name **envyng**.

Have it install the latest (by envyNG supported) drivers, and tell it to automatically configure xorg.conf when it's done.

---

### Post by Rocket2DMn on 2008-04-26
I don't think that cards will run the restricted drivers appropriately.  Since you are currently running the open source ati drivers, you should check this short HowTo on enabling Compiz Fusion with these drivers - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by nami on 2008-04-27
Why has it become so complicated?  In 7.10, I installed nothing and just modified the xorg.conf file to get it to work nice and smoothly...

What is going on?

---

### Post by Rocket2DMn on 2008-04-27
Compiz blacklisted the open source ati drivers because of some bug, and did not have the time or manpower to go through and individually test cards that require this driver (most likely since they only run on older cards).  I guess they figured it wasn't stable enough to be considered a stable release.

---

