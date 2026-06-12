---
title: "Startup sequences, runlevels"
date: 2007-05-04
forum: General Help
---

### Post by thinkbox on 2007-05-04
Hi, I've been using linux for a total of about 4 days. I have an eVGA nVidia 8800GTS 640MB video card, Athlon 64 X2 5200, and have installed the AMD64 release of Ubuntu. I was having issues with the video not working when I booted up, but with some tinkering found that, with a fresh install, disabling the "nv" drivers in the linux-restricted-modules-common file, installing the nVidia released drivers from their website, booting into the single-user/recovery console and then running a telinit 2 starts up the window manager with full display acceleration, and NO issues at all with Beryl, Emerald, or even windows games under Wine.

   I have tried checking the startup procedures for different runlevels using the sysv-rc-conf tool to no avail. Any other procedures that I might be able to try to distinguish the difference between the overall boot procedure of 'Single user>telinit 2' in comparison with a standard boot which apparently boots directly into runlevel 2 under Ubuntu?

   I have to say, I'm a microsoft MCP and MCSE, and I really feel like a noob all the sudden. lol | any help would be greatly appreciated.

---

