---
title: "System freeze every few days"
date: 2012-11-07
forum: General Help
---

### Post by vtrader on 2012-11-07
I have ubuntu running on a thinkpad t400 with intel 4000hd graphics chip.
It's a long story so let me start with what happened first, before while running any window/desktop every few days the dri aspect would segfault, so I would be left with windowless desktops. 
So I update the intel drivers to the latest ppa version. Now I have different problems, every few days I would get what looks like a hard system lock. The screen would just lockup, cannot ctl-alt-f to anything. The first few times I thought it was a complete system lock for which I would have to do a hard shutdown by holding the power button.
The next time I decided to try something else, I ctl-alt-f2 and under the assumption it was the screen that was locked. Of course the screen remained as it was, but I entered my name and passowrd and then did reboot, to my supprise the system reboot.
So the system is not itself in a hard lock freeze, just the display. So I am guessing I am having the same problems as before except this time the drivers are killing the entire screen instead of just the dri.
I checked the logs nothing except in kern.log which say compiz segfault. But this happens even in a simple wm such as fluxbox.

Any ideas?

Thanks,

---

### Post by vtrader on 2012-11-08
Ok, so I used gnome3 this time, left it overnight to stream a flash movie, woke up found the screen blank as if stuck in screen saver mode.
Luckly I was able to ssh via my tablet to see what was going on, there were no error or failure messages, I killed Xorg that did nothing the screen still remained blank, in the end I just rebooted from the tablet.
I think it must be some kind of graphics chip error in the kernel but I get no error messages in any of the logs, the system is not frozen but it is as if the graphics is.
Any ideas?

---

