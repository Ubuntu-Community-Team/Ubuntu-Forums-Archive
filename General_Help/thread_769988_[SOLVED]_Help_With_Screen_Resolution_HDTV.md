---
title: "[SOLVED] Help With Screen Resolution HDTV"
date: 2008-04-27
forum: General Help
---

### Post by czechman86 on 2008-04-27
Hi All!

I just built my new comp and installed 8.04 Ubuntu and its beautiful, except for this stretched out resolution on my HDTV. its my only monitor, so I have no other choice but to use it. right now, I am running it 1024x768, however, the screen resolution should be at 1366x768. I have tried adding the Mode line and the resolution to my xorg, but that only caused all kinds of problems. Does anyone know of any solutions for this?

Here is my graphics card type:
ATI  RS690 [Radeon X1200 Series]

Other info that is needed, please ask. Thanks a million!!!

EDIT: I have done some research, but as of yet, have found anything of little use.

---

### Post by irifan on 2008-04-27
run sudo displayconfig-gtk in a terminal window to configure your monitor and graphics card.

If your monitor is not listed here, please go to the manufactures homepage to get the horizontal an vertical range there.

---

### Post by Cresho on 2008-04-27
are you sure your monitor supports this resolution?  I just went from a 32 inch down to a 24 inch HP w2408 just because it was horrible to view it.  Do as the above guy says.  I was unable to force my HD monitor to use that resolution in windows nor in linux.  1280x720 was the only way for me.  with my 24 inch, i have 1920x1200

---

### Post by czechman86 on 2008-04-27
> **Cresho said:**
> are you sure your monitor supports this resolution?  I just went from a 32 inch down to a 24 inch HP w2408 just because it was horrible to view it.  Do as the above guy says.  I was unable to force my HD monitor to use that resolution in windows nor in linux.  1280x768 was the only way for me.  with my 24 inch, i have 1920x1200

first of all, thanks to both you guys. i tried that particular sudo, however it did not work. when i run 1280x800, i cant see all my screen. like some parts of the pannels are no visible (to the point where it doesnt work). and as for the monitor supporting the resolution, I am sure that it does, for when i hit info on my controller is says either 1024x768 or 1366x768, depending on which mode i am in. could it be said that the best solution might be tolerating 1024x768 and saving up and getting a dedicated computer monitor? or do you think that there is another work around? thanks again!

---

### Post by czechman86 on 2008-06-02
I kind of solved this thanks to some digging through the Ubuntu archives. Although I am not running Ubuntu anymore, I figure that this xorg might be helpful to anyone is having to deal with an HDTV + ATI. The solution is not a definite fix (there are some other problems, but I believe those are related to my tv), but it does help for taking full advantage of you HDTV. I just added every possible monitor mode possible to my xorg and viola 1366x768.

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath      "/usr/share/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/misc"
    FontPath     "/usr/share/fonts/100dpi:unscaled"
    FontPath     "/usr/share/fonts/75dpi:unscaled"
    FontPath     "/usr/share/fonts/TTF"
    FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
    Load  "glx"
    Load  "xtrap"
    Load  "record"
    Load  "GLcore"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
    Load  "freetype"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      330   200    # mm
    Identifier   "Monitor0"
    VendorName   "PTS"
    ModelName    "1911-TLXB"
 ### Comment all HorizSync and VertRefresh values to use DDC:
    HorizSync    30.0 - 80.0
    VertRefresh  56.0 - 75.0
    Option        "DPMS"
    UseModes     "Modes0"
EndSection

Section "Modes"
    Identifier "Modes0"
    Modeline "1680x1050" 181.61 1680 1792 1976 2272 1050 1051 1054 1095
    Modeline "1680x1050" 178.96 1680 1792 1976 2272 1050 1051 1054 1094
    Modeline "1680x1050" 176.48 1680 1792 1976 2272 1050 1051 1054 1094
    Modeline "1600x1024" 168.40 1600 1704 1880 2160 1024 1025 1028 1068
    Modeline "1600x1024" 165.94 1600 1704 1880 2160 1024 1025 1028 1067
    Modeline "1600x1024" 163.64 1600 1704 1880 2160 1024 1025 1028 1067
    Modeline "1600x1000" 164.46 1600 1704 1880 2160 1000 1001 1004 1043
    Modeline "1600x1000" 162.05 1600 1704 1880 2160 1000 1001 1004 1042
    Modeline "1600x1000" 159.80 1600 1704 1880 2160 1000 1001 1004 1042
    Modeline "1400x1050" 151.56 1400 1496 1648 1896 1050 1051 1054 1095
    Modeline "1400x1050" 149.34 1400 1496 1648 1896 1050 1051 1054 1094
    Modeline "1400x1050" 147.27 1400 1496 1648 1896 1050 1051 1054 1094
    Modeline "1280x1024" 134.72 1280 1368 1504 1728 1024 1025 1028 1068
    Modeline "1280x1024" 132.75 1280 1368 1504 1728 1024 1025 1028 1067
    Modeline "1280x1024" 130.91 1280 1368 1504 1728 1024 1025 1028 1067
    Modeline "1440x900" 132.71 1440 1536 1688 1936 900 901 904 939
    Modeline "1440x900" 130.75 1440 1536 1688 1936 900 901 904 938
    Modeline "1440x900" 128.93 1440 1536 1688 1936 900 901 904 938
    Modeline "1280x960" 126.27 1280 1368 1504 1728 960 961 964 1001
    Modeline "1280x960" 124.54 1280 1368 1504 1728 960 961 964 1001
    Modeline "1280x960" 122.69 1280 1368 1504 1728 960 961 964 1000
    Modeline "1366x768" 106.19 1368 1448 1592 1816 768 769 772 801
    Modeline "1366x768" 104.73 1368 1448 1592 1816 768 769 772 801
    Modeline "1366x768" 103.15 1368 1448 1592 1816 768 769 772 800
    Modeline "1280x800" 104.35 1280 1360 1496 1712 800 801 804 835
    Modeline "1280x800" 102.80 1280 1360 1496 1712 800 801 804 834
    Modeline "1280x800" 101.37 1280 1360 1496 1712 800 801 804 834
    Modeline "1152x864" 102.08 1152 1224 1352 1552 864 865 868 901
    Modeline "1152x864" 99.64 1152 1224 1344 1536 864 865 868 901
    Modeline "1152x864" 98.15 1152 1224 1344 1536 864 865 868 900
    Modeline "1280x768" 99.17 1280 1352 1488 1696 768 769 772 801
    Modeline "1280x768" 97.81 1280 1352 1488 1696 768 769 772 801
    Modeline "1280x768" 96.33 1280 1352 1488 1696 768 769 772 800
    Modeline "1024x768" 79.52 1024 1080 1192 1360 768 769 772 801
    Modeline "1024x768" 78.43 1024 1080 1192 1360 768 769 772 801
    Modeline "1024x768" 77.25 1024 1080 1192 1360 768 769 772 800
    Modeline "1280x600" 76.04 1280 1336 1472 1664 600 601 604 626
    Modeline "1280x600" 75.00 1280 1336 1472 1664 600 601 604 626
    Modeline "1280x600" 73.84 1280 1336 1472 1664 600 601 604 625
    Modeline "1024x600" 61.42 1024 1080 1184 1344 600 601 604 626
    Modeline "1024x600" 59.86 1024 1072 1176 1328 600 601 604 626
    Modeline "1024x600" 58.93 1024 1072 1176 1328 600 601 604 625
    Modeline "800x600" 47.53 800 840 920 1040 600 601 604 626
    Modeline "800x600" 46.87 800 840 920 1040 600 601 604 626
    Modeline "800x600" 46.15 800 840 920 1040 600 601 604 625
    Modeline "768x576" 43.52 768 800 880 992 576 577 580 601
    Modeline "768x576" 42.93 768 800 880 992 576 577 580 601
    Modeline "768x576" 42.26 768 800 880 992 576 577 580 600
    Modeline "640x480" 29.84 640 664 728 816 480 481 484 501
    Modeline "640x480" 29.43 640 664 728 816 480 481 484 501
    Modeline "640x480" 29.03 640 664 728 816 480 481 484 501
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "DDCMode"                # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "DynamicClocks"          # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon X1200 Series"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
EndSection
```

Good Luck! If you have anything further to add, let me know. The main other problem that I experienced was that I need to run 1366x768 at 60Hz, however, I could not configure for that and was forced to run at 71.

---

