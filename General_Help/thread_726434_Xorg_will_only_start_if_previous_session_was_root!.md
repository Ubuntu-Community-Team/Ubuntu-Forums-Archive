---
title: "Xorg will only start if previous session was root?!"
date: 2008-03-16
forum: General Help
---

### Post by superatrain on 2008-03-16
I have a Ubuntu install with a weird Xorg issue. My laptop wouldn't load the 7.04 Ubuntu/Kubuntu CDs, (Latest release at that point) or the 6.10 Ubuntu CD, so I installed 6.10 Kubuntu. I had big troubles with the 6.10 -> 7.04 upgrade, as for some reason, something failed, the machine crashed, and I had to finish the upgrade by hand. Eventually, I recovered the machine, but only after finding out that the /tmp folder had its permissions changed to root only (chmod 007). Now, I'm running 7.10 Ubuntu. (from 7.10 Kubuntu, which had the same issue as this). The upgrade (7.04->7.10) seemed to go fine, no error messages or anything.

The problem is, when booting up normally, Xorg flashes on for a second (see mouse cursor), then hangs indefinitely with a blank screen. The only option is to hold down the power button :(. When I boot up into recovery mode, and run startx, it works perfectly (aka: xorg.conf is fine.) If I reboot, the machine loads gdm fine. But, if I reboot again, it won't work again, until I go into the recovery mode, etc...

I'm wondering, what could be causing this? I would much rather get down to the root of the problem than to just reinstall Ubuntu. My only guess would be that something else has the wrong permissions, but I have no clue where to start looking.

Any ideas?

---

