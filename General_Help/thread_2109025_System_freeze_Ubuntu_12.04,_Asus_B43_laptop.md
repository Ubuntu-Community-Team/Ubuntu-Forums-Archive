---
title: "System freeze: Ubuntu 12.04, Asus B43 laptop"
date: 2013-01-26
forum: General Help
---

### Post by iowabeakster on 2013-01-26
My wife's computer: (disregard the Xubuntu stuff in my profile... that is my machine)

The problem is a random system freeze.  It might be days between episodes, or it might happen within a half-hour of the previous episode. It is not a sleep/wake-up problem (those work fine), it happens while machine is actively being used.   It is not application specific.  

Touchpad and keyboard are completely unresponsive.  I cannot get to a tty (ctl-alt-f1).  I cannot do a "safe" shutdown (alt-sysrq-R-E-I-S-U-B).

The only option is a hard shut-down.

Asus B43S-xh51
Intel i5-2520
Ubuntu 12.04 (current and past supplied generic kernels plus a couple of newer other kernels from Ubuntu-mainline that I tried)

It is using the integrated Intel 3000 graphics (the ATI 6470 card is still not supported... boo).

The system logs are not showing anything... just things working fine, then the reboot.  (but I am CERTAINLY not any kind of expert debugger)

I thought the problem was a GPU lockup, and wanted to provide some good debugging info for assistance. I found this:

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze")

So this morning when it froze, I tried to ssh into it from my machine.  But I cannot even do that.  It was unavailable to ssh.  I checked my modem/router and it was not even connected (although it was when it froze).

Apparently (to my untrained eyes) it more than a GPU lockup.

Any help or suggestions?

---

### Post by iowabeakster on 2013-01-28
A few more freezes over the last few days.  Still cannot get access to system via ssh, while frozen.  After every freeze I check syslog and kernelog.  No errors... 

I have noticed that the last entry before the last couple of freezes has been a cron job.  One was a monthly (with no monthly jobs scheduled) the other was an hourly.  But there were no errors and both were several minutes prior to the freeze.  I am guessing just coincidence.

Updated it to 12.10 (standard supplied kernel), had a couple of freezes with 12.10 yesterday too.

The freezes can happen while doing anything: browsing, libreofffice work, etc.  Yesterday one happened while watching netflix.  The sound just repeated/skipped perpetually like a cd player that cannot get past a bad scratch or something.

---

### Post by itwerks on 2013-02-23
*bump*

I can report similar misbehaviour, 12.10 32bit, fresh install, Nvidia GeForce 9500 GT, Biostar mobo... For at least the last month, possibly two months, my system has been completely unstable.  It ran rock solid for well over a year and then I started experiencing gnome-shell crashes, shortly thereafter the system began acting odd.  I'll lose the ability to interact with any desktop elements, sometimes my mouse pointer will be frozen, often it is not, but again, I can not interact with any windows.  Can't get to tty via ctrl-alt-f1, can't ssh into the box... I can however use REISUB to reboot.

I see nothing that points to any error in my syslogs. kern.log seems fine (other than a persistent update-notifier segfault).  Xorg.0.log shows no issues whatsoever.

I have no idea how to move forward troubleshooting this issue.  bump for great justice.):P

---

### Post by iowabeakster on 2013-02-23
Changed to XUbuntu on the laptop a few weeks ago, freezes continue.  Underclocked the CPU, freezes continue.  Fan speeds sensors could not be recognized/contrlloed by Linux kernel modules.  Used Windows to modify stock bios fan speeds and temp thresholds and flashed the modded bios.  Temp sensors reported cooler temps.  Ubuntu still froze up randomly well below critical thresholds.

---

### Post by iowabeakster on 2013-03-29
I noticed while running standard Ubuntu 12.10 (changed back again today... with a totally fresh install) that the AMD graphics card was running at a smoking 82C (!!!) at idle (within a minute of boot).  Of course it only gets hotter from there!

I've monitored temps in the past because of system freezes, and the AMD card had always been near the temp of all of the rest of the internals.  The temperatures never before indicated that the shut downs were temperature related.
 
This is running the default open source driver, on a fresh install.  The video card clock speed must be pegged out of the box.  Awesome... 
 
Still, proprietary drivers just won't work at all, even from jockey (I've tried it all... maunal intstall...build debs for manual install... alternaive PPAs).  The best of those results in "low graphics mode".   If you consider "low graphics mode" to be a completely unusable pop-up gui menu that is unresponsive to all input.
 
... temporarily resolved by completely disabling dGPU with switcheroo...

Desperate plea to the people in charge at Ubuntu:  Please stop all development on flashier graphics, reinventing the desktop, creating new features, expanding to new hardware systems (phones and tablets), and simply make the current distributions stable again (or if not stable... at least safe to run without damaging your hardware).  

Thanks for the memories.

---

