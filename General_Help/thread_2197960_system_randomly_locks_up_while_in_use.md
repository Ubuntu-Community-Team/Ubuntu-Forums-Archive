---
title: "system randomly locks up while in use"
date: 2014-01-06
forum: General Help
---

### Post by Derek_Gentle on 2014-01-06
Hi All

Been having nothing but trouble with one of my new desktops.  It's a small mITX system that I am using in the living room.  I currently have Kubuntu 13.10 installed. Only XBMC has been added as a third party repo.

ASUS H81I-PLUS Socket 1150 w/ Intel H81 Chipset 
Intel Pentium G3220 Dual-Core Processor @ 3.0 GHz
Team Vulcan 8GB (2 x 4GB) 240-Pin DDR3 1600  (*under clocked to 1333 by the BIOS*)
Intel 330 Series 60GB SSD

I originally had openSUSE 13.3 installed, but was having a different set of problems.  I then installed Kubuntu 13.10, and for the most part it *seemed* to be running fine.  Then the lock ups started to occur. At first I thought it was XBMC as at the time, there was not a supported version for 13.10.  This has since been resolved by the release of XBMC 12.3.

It got to the point where the desktop would lock up on YouTube, running Amarok or playing a media file through VLC.  Finally, the system would boot and freeze on the login screen.  The HD light on the box being on solid.
When the system would freeze, it would lock up the entire box as the system was inaccessible even through SSH.

Last night I completely reinstalled the entire OS and it appeared to run fine over night.  I started up Amarok this morning, set the mysql details, and the system locked up.

As someone who has never had an issue with any of his *nix installations, I am unsure as to where to check (logs, etc) for error messages and/or pointers in the right direction.

---

### Post by mike99-5 on 2014-01-06
I am also having these problems since updating to 13.10.

Things don't actually lock up during boot, it simply takes ages to boot. The hard drive light stays on solid and the system does not respond, but if you wait long enough the drive light begins to flicker and things eventually get back to normal.

However, when watching video material on YouTube or from the HD using the default video player, it often, but not always, crashes. I then must switch off and on again.

Using 12.xx on the same unit I never had these problems so it makes 13.10 a bit of a pain.

Any ideas would be thankfully received...

---

