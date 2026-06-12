---
title: "Has Ubuntu 14.04.01 LTS broken my laptop?"
date: 2014-12-28
forum: General Help
---

### Post by felichas on 2014-12-28
Hi,

My laptop: HP Pavillion dv6000. 
Core2 Duo T5750, 2GB RAM, GeForce 8400M, Dual Boot Windows/Ubuntu 14.04.01 i386

Linux installed recently. It all worked fine until I closed the lid and the computer went into suspension mode (default behaviour).
After opening the lid and waiting more than expected I wrote my password, and got the desktop but never the launcher. 
[CTRL][ALT][F1..F5] did not work either and all I could do was using [Magic SysRq]("http://en.wikipedia.org/wiki/Magic_SysRq_key") to restart it. 

Now I have graphic glitches on BIOS screens. 
Loading BIOS defaults did not help. 
Mem test says RAM is ok
Linux boots fine but resolution is only 1024x768 / 800x600 (software driver).
After booting Ubuntu internal error menu pops up.

Looks like the suspension has corrupted something that afects my graphic card.
Any help will be greatly appreciated.

PS.- The yellow boxes in the pic are new. BIOS setup is also very hard to read for the same reason.

---

### Post by Portaro on 2014-12-28
Did you install any proprietary graphics card driver?

What is the model of your graphic card?

Other info - You pc produces any sound "beeps" when you launch the system?

Dont change Bios or options of BIOS at this time, maybe is graphic card and if is this there are no problem with BIOS or hardware is only bad config of Xorg or X or corrupt boot kernel default with this graphic driver mode.

So, just wait other users with more knowledge that I have to solve the problem.

---

### Post by felichas on 2014-12-29
> **Portaro said:**
> Did you install any proprietary graphics card driver?

What is the model of your graphic card?

Other info - You pc produces any sound "beeps" when you launch the system?

Dont change Bios or options of BIOS at this time, maybe is graphic card and if is this there are no problem with BIOS or hardware is only bad config of Xorg or X or corrupt boot kernel default with this graphic driver mode.

So, just wait other users with more knowledge that I have to solve the problem.


Graphic drivers for my GeForce 8400M were default as per installation. Nouveau, I believe. 
No beeps, but graphic glitches from the very moment I boot the machine.
Same problem the windows installation, resolution went to safe default (1024x768).

---

