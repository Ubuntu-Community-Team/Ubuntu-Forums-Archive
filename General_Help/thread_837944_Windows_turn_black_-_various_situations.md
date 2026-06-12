---
title: "Windows turn black - various situations"
date: 2008-06-23
forum: General Help
---

### Post by rhardie on 2008-06-23
I attempt to reply to email and my screen is black.  I can click on the black screen and see a transparent view of what I "should" be seeing.

The black screen occurs at other times - sometimes when attempting to view a web page.

This didn't always happen but began after one of the many Synaptic upgrades a while back.

I thought it was a memory issue and upgraded from 1 GB to 3 GB of RAM with no change in symptoms.

I can close out various applications and get the display to work correctly (thus my original thoughts on memory issues).

AMD Athlon 64 3200
3 GB RAM
Hardy Heron (8.04) 64 Bit Desktop
GeForce FX 5700LE
Dual Monitor
Compiz enabled

---

### Post by Zorael on 2008-06-23
This may be the infamous Nvidia "Black Window bug". Are you running  their proprietary drivers? If so, it's Compiz running out of video memory. It was Supposed™ to have been fixed some driver versions back (100.14.19?), and if you have an old card this driver may not work with it. [Yours is eligible for the new one, though.](http://www.nvidia.com/object/IO_18897.html)

There is supposedly a fix which you can try. Just make sure to backup your /etc/X11/xorg.conf before making modifications to it.

Compiz-Fusion forums: [Fix the Black Windows Bug, Frozen Bug and Special Setup nVidia cards!](http://forum.compiz-fusion.org/showthread.php?t=1762)
OpenSUSE wiki: [Nvidia Black Window Bug Fix](http://en.opensuse.org/Nvidia_Black_Window_Bug_Fix)

---

### Post by rhardie on 2008-06-23
Well, interestingly enough, my desktop now has developed a new problem: The tool bar and menu bar have disappeared.  This means I'd have to command line all of my fixes and I'm not skilled enough for that and don't have the time to learn in the short term.

The Nvidia bug sounds "reasonable" and I am running thier non-free drivers.  I'll check it out as soon as I get my tool/menu bars back on my Gnome desktop.

Thank you and kind regards,

Rocky

---

### Post by rhardie on 2008-07-19
Yes, I am running Compiz and proprietary drivers for nVidia GeFORCE 5700LE.  It sounds like maybe I should upgrade my video card.

I've been running Ubuntu for my financial services business and it has been like a breath of fresh air.  No system crashes or antivirus software to slow me down.

Thanks for your response to my challenge.

Rocky

---

