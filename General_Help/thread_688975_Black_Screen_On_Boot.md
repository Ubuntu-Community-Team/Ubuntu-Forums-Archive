---
title: "Black Screen On Boot"
date: 2008-02-05
forum: General Help
---

### Post by osiris2258 on 2008-02-05
I am unable to use Ubuntu!

Every time I boot up, after going through all of the checks and the boot splash (I removed quiet from my boot spec, but I don't see any errors occurring), Instead of the login screen I get nothing. Completely black, my monitor even goes to sleep from lack of signal. The processing light on my tower is still going, but nothing ever happens (I tried leaving it for a half hour, still nothing). Booting into recovery mode works, but I don't know what is causing the problem. Maybe something with X?

My system setup is Gusty in dualboot with XP, nVidia Geforce 7600GT with proprietary driver, 2GB ram, Athalon 64X2 Dual 4600+. I have been able to run Ubuntu fine up until this last week or so. I already tried reinstalling, running from the CD worked fine and it booted up properly once before it started doing the black screen again.

Anybody have any idea what is causing this & how to fix it? :confused:

---

### Post by jken146 on 2008-02-06
Type ```
startx
``` in recovery mode and see what happens.

---

### Post by osiris2258 on 2008-02-07
Yeah, it's X alright. Using ```
startx
``` in recovery mode immediately brings me back to the black screen. I am not sure what to do now that I know about this, though, since I know nothing about X.

---

