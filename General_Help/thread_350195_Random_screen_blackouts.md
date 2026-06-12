---
title: "Random screen blackouts"
date: 2007-01-31
forum: General Help
---

### Post by dad311 on 2007-01-31
Several weeks ago I purchased a new monitor(viewsonic VX2035).  Since that time, Ive started getting random screen blackouts.  I dont believe its a screensaver issue because it happens while im typing.

I have found that if I do a shutdown then a power on,  will clear the problem.  Howerver a reboot causes the problem to reappear.

Also I no longer see the bootup progress on the monitor.  The monitor reports "out of sync" while Ubuntu is booting.

Has anyone had any of these issues or know how to resolve them?


Thank you.

---

### Post by Theimon on 2007-01-31
You're using the old xorg.conf file with the new monitor. Probably the sync-rates for the old monitor are still in there.
Open a terminal and do:
```
dpkg-reconfigure xserver-xorg
```
It will probably recognize your monitor and hence its sync-rates, if not you can manually add them (you have to look them up first ofcourse).
Good luck.

---

### Post by dad311 on 2007-02-01
I did a scratch load when I installed the new monitor.  I also edited my xorg.conf file to reflect the monitors settings, see below.   Does this look correct?  

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

**FROM VIEWSONIC WEB SITE:**
VIDEO INPUT  	Analog/Digital  	RGB analog (75 ohms, 0.7 Vp-p); DVI-D
Frequency 	Fh: 30~82kHz, Fv: 50~85Hz
Sync 	H/V separated (TTL), composite, sync-on-green

---

### Post by dad311 on 2007-02-03
SOLVED

Looks as if my video card(geforce 6200tc) was bad or could not handle 1680x1050 resolution.  I replaced the video card with a geforce 6600 GT and the problem is resolved.

---

