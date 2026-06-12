---
title: "Help enabling 2nd monitor in xorg config"
date: 2020-09-24
forum: General Help
---

### Post by getut on 2020-09-24
I've been on a broader search to get Nvida G-Sync working on a laptop and have succeeded, but have one last issue getting my 2nd monitor to work at the same time as the G-sync config. If you want to read long posts on where I am here is the thread [https://ubuntuforums.org/showthread.php?t=2450746](https://ubuntuforums.org/showthread.php?t=2450746).

But for this particular problem, I think a synopsis will do. Laptop with 2nd monitor attached. Due to G-Sync requirements I ended up having to go with explicit xorg configuration rather than letting xrandr or other methods do their thing. I also did not use xorg.conf in /etc/X11 but opted to go with a 10-monitors.conf file in /usr/share/X11/xorg.conf.d.

The laptop screen is working as needed with the below in the 10-monitors.conf file. The Dell on HDMI-0 is completely non-functional. I built the monitors section for the Dell by using edid decode.

10-monitors.conf
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "DP-4"
    VendorName     "Unknown"
    ModelName      "AU Optronics Corporation"
    HorizSync       266.6 - 266.6
    VertRefresh     60.1 - 240.0
    Option         "DPMS"
    Option         "UseEdid" "false"
        Modeline        "Mode 0" 533.28 1920 1968 2000 2000 1080 1090 1095 1111 -hsync -vsync
        Modeline        "Mode 1" 533.28 1920 1968 2000 2000 1080 1090 1095 4440 -hsync -vsync
EndSection

Section "Monitor"
        Identifier "HDMI-0"
        ModelName "DELL U2414H"
        VendorName "DEL"
        DisplaySize 530 300
        Option "DPMS" "true"
        Horizsync 30-83
        VertRefresh 56-76
        # Maximum pixel clock is 170MHz
        #Not giving standard mode: 1152x864, 75Hz
        #Not giving standard mode: 1280x1024, 60Hz
        #Not giving standard mode: 1600x900, 60Hz
        #Not giving standard mode: 1600x1200, 60Hz
        #Not giving standard mode: 1920x1080, 60Hz

        #Extension block found. Parsing...
        Modeline        "Mode 13" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 2" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
        Modeline        "Mode 3" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
        Modeline        "Mode 4" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
        Modeline        "Mode 5" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
        Modeline        "Mode 6" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
        Modeline        "Mode 7" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
        Modeline        "Mode 8" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
        Modeline        "Mode 9" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
        Modeline        "Mode 10" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 11" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
        Modeline        "Mode 12" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
        Modeline        "Mode 14" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
        Modeline        "Mode 15" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
        Modeline        "Mode 16" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync
        Option "PreferredMode" "Mode 13"
        Option "RightOf" "DP-4"
        Option "Position" "1920 0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "nvidia"
    Monitor        "DP-4"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DP-4: 1920x1080_240 +0+0 {AllowGSYNCCompatible=On}, HDMI-0: 1920x1080_60 +1920+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by TheFu on 2020-09-25
The only reason that I'd prefer /etc/X11/... over  /usr/share/X11/xorg.conf.d/ is because I backup everything in /etc/, but I backup NOTHING /usr/share/.
Functionally, it wouldn't matter.

---

### Post by getut on 2020-09-27
> **TheFu said:**
> The only reason that I'd prefer /etc/X11/... over  /usr/share/X11/xorg.conf.d/ is because I backup everything in /etc/, but I backup NOTHING /usr/share/.
Functionally, it wouldn't matter.

Any hints on what is wrong with my Dell monitor config that will get it running? I HAVE to have use edid false on the laptop screen to have G-Sync functional on it but it's almost acting like useedid false turns it off for BOTH monitors and the Dell is not picking up its specific config for some reason.

---

### Post by TheFu on 2020-09-27
Sorry, no. I responded **only** about the location of config files.

I know nothing about g-sync and my nvidia dual monitor system if fairly complex due to some unusual connection requirements here.

---

