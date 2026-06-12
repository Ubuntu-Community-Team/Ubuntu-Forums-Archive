---
title: "How to determine (and change) color depth? [Kubuntu feisty]"
date: 2007-05-08
forum: General Help
---

### Post by size_XXM on 2007-05-08
The question's in the topic name, so.. any ideas? Before you advise me to edit ***defaultdepth***in xorg.conf - done that, no change. I even ran the nvidia-xconfig utility:```
nvidia-xconfig -d 16
``` and no change. As for how do I know it hasn't changed - I go [_here_](http://www.parfaitimage.com/Images/Grayscale.jpg) and check whether the color transition is smooth (still 24 bit) or chunky (16 bit). What do I need to do - change the modeline or what? If so, can someone point out a decent guide how to do that?

The reason why I want to do this is that read somewrhere you can have 3D desktop even on nvidia GF2MX with satisfactory speed, if you decrease the depth. :-D Hell, i HAD the 3D desktop on GF2MX400 back when I tried the Kororaa liveCD (although it crashed when I tried to play video - probably bad drivers back then), and would LOVE to have it again.

---

### Post by size_XXM on 2007-05-08
the display-related sections in my xorg.conf:
```
Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic"
    ModelName      "Flat Panel 1680x1050"
    HorizSync       31.5 - 90.0
    VertRefresh     60.0 - 60.0
    Gamma           1
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 # 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "ProbeAllGpus" "True"
    SubSection     "Display"
        Virtual     1920 1200
        Depth       16
        Modes      "1680x1050@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60"
    EndSubSection
EndSection

Section "Screen"
 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    16
EndSection
```

---

### Post by size_XXM on 2007-05-19
BUMP!
no one?

---

