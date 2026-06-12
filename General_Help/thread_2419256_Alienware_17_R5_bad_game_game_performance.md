---
title: "Alienware 17 R5 bad game game performance"
date: 2019-05-18
forum: General Help
---

### Post by arbitrarydepth on 2019-05-18
So I've got this great gaming laptop that works great on windows, but I wanted to dual boot ubuntu 18.04 and maybe see if I could even game a little on it with albion online. When i installed albion tho, it performed very badly, with bad frame rate and the mouse being almost inoperable as long as the game was running as i tried my best to drag it across the screen.
i suspect this is not the games fault and is to do with drivers and support of my hardware, but I want a professional opinion and maybe some insight into what my options are to maybe getting this baby purring on linux.

---

### Post by DuckHook on 2019-05-18
Unfortunately, I am the bearer of bad news…

[LIST=1]
[*]Gaming and Linux are not good bedfellows. Most games are made only for Windows. Linux is Not Windows (see my sig). Hence, Linux and games don't mix.
[*]The default drivers for most GPUs are open-source drivers designed for stability; not performance. Moreover, they are to a large extent reverse engineered and therefore not optimized to take advantage of unpublicized HW oddities that GPU OEMs build into their cards.
[*]For better performance, many users will install closed-source proprietary graphics drivers to replace the defaults after their initial install, but even these usually lag behind the drivers made available to Windows.
[*]A few games work well in WINE, but not a lot.
[*]Older games work in a Windows VM running within a Linux host, but the added overhead of a VM plus the primitive emulated graphics card makes anything but old games feel sluggish or downright unplayable.
[*]Steam has come to the rescue with a stable of games that have been ported to run natively in Linux. However, the selection is not as extensive as it is for Windows.
[/LIST]
The upshot is that if gaming is central to your computer usage, Linux is not a good platform for you. But if stability, reliability and productivity are your primary concerns, then Linux more than holds its own.

---

### Post by CatKiller on 2019-05-19
You haven't said whether you've installed the Nvidia drivers, nor whether you're using those graphics rather than your integrated Intel ones. Those are both critical pieces of information.

---

