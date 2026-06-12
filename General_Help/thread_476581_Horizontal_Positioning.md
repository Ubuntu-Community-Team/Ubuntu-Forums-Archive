---
title: "Horizontal Positioning"
date: 2007-06-17
forum: General Help
---

### Post by mrBobDobalina on 2007-06-17
I have a widescreen monitor that is very stubborn about positioning my desktop a few hundred pixels to the left. I can fix the problem by selecting a resolution that the monitor doesn't support, which will blank out the monitor and force an autodetect (I'm assuming). When it resumes the desktop is correctly positioned. I've installed the xserver-xorg-video-intel driver and I've attempted to force the configuration through xorg.conf, but after restarting the xserver the monitor position is always offset to the left. Anyone else having this issue? Is the problem with the xserver configuration, the display driver or possibly even the monitor itself? Any help would be appreciated.

Some details:
Xubuntu 7.04 (Feisty)
Installed xserver-xorg-video-intel
Monitor: Dell SE198WFP
Display controller: Intel 82P965/G965

installing the intel driver gives me the proper resolution even though there is no option for 1440x900 @60Hz in Applications->Settings->Display Settings. There is an option for 1440x900@75. Below is the relevant section of my xorg.conf

Section "Device"
    Identifier    "Intel Driver"
    Driver        "intel"
    BusID        "PCI:0:2:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Dell"
    Option        "DPMS"
    HorizSync    30-83
    VertRefresh    56-75
    Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934  -hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Driver"
    Monitor        "Dell"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by gnirts on 2007-06-18
Does that monitor have an auto-adjust button/feature? Can you use the monitors OSD to move the desktop over?

---

### Post by mrBobDobalina on 2007-06-18
The monitor's OSD won't compensate enough. The setting defaults to 50 with the max movement to the right being a value of 100. I don't know what the scale is, but it doesn't appear to be pixels. Even when set at 100 (all the way to the right) a good portion of the desktop is still off screen.

---

### Post by mrBobDobalina on 2007-06-22
as gnirts suggested the monitor auto adjust does fix the problem. I decided to boot into the windows partition and noticed that I'm having the same issue there, so the problem is either with the monitor itself or the video card. I'm now finding that the screen is sometimes positioned correctly when I boot up, and sometimes I still need to force an auto adjust. I can live with that.

---

