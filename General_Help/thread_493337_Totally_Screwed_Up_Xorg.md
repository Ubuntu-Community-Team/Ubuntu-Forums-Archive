---
title: "Totally Screwed Up Xorg"
date: 2007-07-05
forum: General Help
---

### Post by cdsboy on 2007-07-05
So i just decided to install ubuntu again and start messing around. I had everything up and running and then i messed around with some stuff. To make a long story short i totally screwed up my xorg.conf files and i had to use dpkg-reconfigure xserver-xorg to get everything up and running. My problem now is that a few things do not work like the should or did. e.g my wireless card no longer works. Is there anyway that i can reconfigure my xorg.conf to reflect what i twas when i installed ubuntu?

---

### Post by cdsboy on 2007-07-05
anybody?

---

### Post by SZorg on 2007-07-05
If you had saved a backup, that would have been your best option. I'm not *entirely* sure that your xorg.conf is causing you the grief; however -- you might do well to run a livecd and copy the cd from the virtual disk (livecd's filesystem) to your own. Back up first, though ;)

---

### Post by DagMan on 2007-07-06
It's odd for the file to effect your wireless interface.  I think it's an unrelated problem.
Maybe you can look at the output of iwconfig to see if there's a wireless interface set up on the computer and if so maybe it needs to be set up.  I've also done some pretty stupid things like spent a good long time trying to troubleshoot the wireless interface when the problem is that there's a switch on my laptop which got bumped into the off postition.  Other little things that get overlooked, to rule out first, is wheather an fn key on a laptop would have shut it off and less obvious is that some people have reported turing it off in Windows and being unable to turn it back on in Ubuntu so having to reboot into Windows again to do it.

Start with just looking at the output of iwconfig and see if there's any interface that doesnt say no wireless extention.

---

