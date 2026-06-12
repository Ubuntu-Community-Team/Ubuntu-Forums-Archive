---
title: "Issues with GDM Screen Resolution"
date: 2007-10-19
forum: General Help
---

### Post by EmyrB on 2007-10-19
Hi all

Just installed Gutsy on my work machine which uses an ATI Radeon 9550. Everything works OK, except for the screen resolution in GDM, I think it is setting it to something like 1900 x 1200. Also Gnome is set to the same resolution (sorry I can't be more specific, I borked up my xorg.config). Anyway I set the resolution in Gnome to the correct resolution 1280 x 1024 and everything is OK, except for GDM which is at the high resolution. If I shut the machine down and reboot after say 5 minutes, then my screen resolution goes back to the very high setting.

I checked my xorg.conf (which is how I borked it) and there is no screen resolutions listed in it. All it has in display is defaultdepth = 24 and that is it.

Any ideas?

Cheers

---

### Post by EmyrB on 2007-10-19
OK UPDATE

Not sure if it is Gutsy that is borked, xserver or the ATI driver.

Reinstalled Gutsy and installed the restricted drivers for my ATI card. Rebooted and logged in. Tried to enable Compiz, but no joy. Can't remember the exact error, but basically xserver-xgl is not installed. So I install it via apt and wants to restart the xserver, which I have no problems with. Then my screen goes black for about 30 seconds and it says there is an error with my graphics settings and Ubuntu is in safe graphics mode. I set my screen resolution to 1280 x 1024 and leave the graphics card as vesa. I reboot to a normal correct screen resolution. I log in and enable the ATI restricted driver. Ubuntu wants to restart and hey, guess what - black screen for 30 seconds and then Ubuntu goes into safe graphics mode and I have to jump the same hoops again.

Basically I end up in a loop. Do ATI cards work with Linux as I have never had this issue with any of the distro's I use at home. All the GFX cards at home are nVidia ones as I prefer them.

Any ideas?

Cheers

---

### Post by btt on 2007-10-19
ATI graphics cards do work, but compiz support is... a little flakey atm, with the proprietry (fglrx) drivers, at least.  Hopefully a new driver will be released in the next few days which will support AIGLX and be all-around better.  You _might_ have better luck with the open-source radeon driver, but I think your card is a little too recent for it (iirc, it only supports <=9200, but I could be wrong).

I have had a load of problems with the proprietry drivers in the past - they seem rather bad at working out what your monitor supports.  Maybe it's just because I have a CRT, rather than a EDID-supporting flatscreen.  Anyway, I'd suggest you add a section to your xorg.conf to specify exactly what modes your monitor supports.  Here's a sample from my file:

```
Section "Monitor"
  Identifier  "Dell D1626HT"
  Option    "DPMS"
  Horizsync 107
  Vertrefresh 48-160
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Device    "Generic Video Card"
  Monitor   "Dell D1626HT"
  Defaultdepth  24
  SubSection "Display"
    Depth 24
    Modes "1600x1200@75" "1280x1024@75" "1024x768@75" "800x600@75" "640x480@75"
  EndSubSection
EndSection
```

Replace the modes with whatever modes your monitor supports (starting with your preferred default), and be very sure to replace my values with your monitor's horizontal / vertical sync values - if you don't you could damage something ;)

If you still can't get a working X display, check /var/log/Xorg.0.log, and look for lines beginning with (EE).  In the past, my problems have been due to fglrx being unable to detect valid screen modes, but there are many other potential problems.

---

### Post by EmyrB on 2007-10-19
Hey thanks btt, I think my problem is also down to the fact that I use a CTX monitor whose model number is not in the list of supported monitors (I set it to an LCD 1280 x 1024).

I tried pitting in modes into my xorg.conf and I kept going into the low-graphics mode, so I took them out and rebooted and well so far it seems to be working except that GDM is still not at the correct resolution. Although I did not add the frequency to the list of modes, maybe I will give that a go :)

I probably will hang on until the new driver is released sometime next week and see if that makes a difference.

---

