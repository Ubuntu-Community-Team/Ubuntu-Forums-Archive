---
title: "Edubuntu screen res oddness"
date: 2007-11-29
forum: General Help
---

### Post by Duo Maxwell on 2007-11-29
Hi, I'm putting together an edubuntu for my aunt, I just installed the restricted nvidia drivers for the riva tnt2 m64 graphics card and oddly the screen res went from 1024x768 @ 60Hz to 800x600 @ 60 Hz with no option to increase either, the screen is an HP M50 info on it starts on page 41
[http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&cc=br&dlc=pt&product=59257&lang=pt&](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&cc=br&dlc=pt&product=59257&lang=pt&)
How can I correct this?

The hardware is an P4 1.6Ghz, asus P4B mobo, 384Mb of PC133, a Riva TNT2 GPU, some old lynsis nic and some modem I pulled from a recent model HP comp that I don't know if it works...

---

### Post by luisfcup on 2007-11-29
You can change the resolution manually by changing you *xorg.conf* file located at */etc/X11*, backup first :p

Look for the Section caled "Screen"
```
Section "Screen"
 Identifier "Default Screen"
 Device "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
 Monitor "Monitor Generico"
 DefaultDepth 24
 SubSection "Display"
  Depth 16
  Modes **"1680x1050"** **"1024x768"**
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes **"1680x1050"** **"1024x768"**
 EndSubSection
EndSection
```

In the "Display" SubSection you can put the modes you what with the respectively color depth, then restart the X with <Ctrl>+<Alt>+Backspace

---

