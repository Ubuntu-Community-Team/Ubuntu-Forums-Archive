---
title: "apt-get upgrade...now my screen is meseed up"
date: 2008-04-07
forum: General Help
---

### Post by 200mg on 2008-04-07
I did an apt-get update and upgrade last week.  The next time i booted the picture on my screen was pushed left leaving a 1 1/2 inch black gap on the right hand side.  I tried the "Auto" config button on my monitor(which has worked in the past), and it does not help.  When i manually try to adjust the settings it's still off by the same amount of space left and right.   I have checked my xorg.conf file and nothing has changed.  Any ideas?  Anyone else have this problem?

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "HW191D"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection

```

---

### Post by kbless7 on 2008-04-07
Look in advanced desktop settings. There are options for screen and window adjustments in there.

---

### Post by 200mg on 2008-04-07
I'm actually using fluxbox, but In Gnome the screen res. only registers up to 1280, but my xorg says 1440.  It's like it doesn't recognize the widescreen.  Any way to fix that?

---

### Post by warp99 on 2008-04-07
> **200mg said:**
> I'm actually using fluxbox, but In Gnome the screen res. only registers up to 1280, but my xorg says 1440.  It's like it doesn't recognize the widescreen.  Any way to fix that?

If you set up a "Generic Monitor" and put the refresh values in for the monitor you can change that to the resolution you want. I have my Niko 22" LCD setup like that because there was no settings for the resolution I wanted, which was 1680x1050. It sets an entry into the xorg.conf like this:

> Section "monitor" #
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1680x1050"
        Horizsync       31.5-65.5
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

Of course back up your xorg.conf **BEFORE** you try this at home.

---

