---
title: "Xinerama Problems with Two Nvidia Cards"
date: 2007-05-27
forum: General Help
---

### Post by sinfree on 2007-05-27
I am having an issue with Xinerama on Two Nvidia cards.  Basically I can set up my xorg file (which I have a lot of experience doing by now) to run with my two video cards (one AGP, one PCI), one monitor for each card.  If I have the Xinerama option enabled then it works ok, but glxinfo returns an error, screensaver/lockscreen doesn't work (even with a 2D or blank screensaver), and 3D apps don't seem to work.  I can comment out the Xinerama option, leaving everything else the same, and everything works fine.  The problem is that with Xinerama commented out if gives me two seperate desktops.  Which isn't so bad, except I can't drag windows across them, and there is no system tray on the second desktop (which I need for using Pidgin/Gaim, Skype, etc).  Plus it won't let me run two seperate instances of Firefox on each desktop (which is just insane).  I don't recall having this issue with any other distro (usually Xinerama worked just fine with 3D accel on my monitor hooked to my AGP card), and I have read where ppl are having similar or related problems with this release of Ubuntu (7.04).  I can also use the same exact xorg file with Xinerama enabled, but just use the nv driver and everything works great (of course with no 3D accel).

I have read that often Xinerama only allows 3D accel on one desktop, which is fine... I don't use Beryl, I just need 3D accel on my AGP card/monitor so I can play GuildWars (which I have working though Wine, yay!) and OpenArena.  I know I could just use nv driver for normal use, then just switch to a different xorg form 3D accel, but that is a terrible solution.  Plus websites, like digg, run slower than Christmas with nv (but work fine with nvidia).

Anybody else have Xinerama working with two video cards (one monitor each) with screensaver/lock screen working, and 3D accel on at least one monitor?

Thanks,
JC

---

### Post by sinfree on 2007-05-28
WOOHOOO!  I solved my problem!  I was trying to use the "nvidia" driver for both cards with problems.  I also tried using "nvidia" for the AGP card and "nv" for the PCI card, which would not work at all.  Finally, I decided in a last ditch effort to swtich to the "vesa" driver for the PCI card (in the xorg.conf file), and leave the AGP as "nvidia" and it workd perfect!  Of course I only have 3D accel on the AGP card, but that is all I need, and everything else works perfect!

---

