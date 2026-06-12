---
title: "Xorg resolution issue on second monitor"
date: 2014-10-18
forum: General Help
---

### Post by d.maarouf on 2014-10-18
Hi Ubuntu Forums,

I have an Acer P215H monitor that I've added as a dual monitor. It won't display any resolutions higher than 800x600 though. The display works perfectly fine in Windows. I've tried adding the resolution to xorg.conf based on the EDID information that I was able to get from a Windows program but it still refuses to display anything about 800x600. I've also tried adding it with xrandr which gives me this error. I should mention that I'm using the proprietary Nvidia driver. 

```

$ xrandr --newmode "1920x1080_60.00" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
$ xrandr --addmode HDMI-0 1920x1080_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  41
  Current serial number in output stream:  42

```

Here is my xorg.conf

```
Section "ServerLayout"    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    DisplaySize     597    336
    HorizSync       88.8 - 88.8
    VertRefresh     59.5
    ModeLine       "2560x1440" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync
    Option         "DPMS"
EndSection


Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Acer"
    ModelName      "Acer P215H"
    DisplaySize     480    270
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    ModeLine       "1920x1080" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Option         "DPMS"
EndSection




Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 780"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "true"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "UseEDID" "False"
    Option         "UseEDIDDPI" "False"
    Option         "UseEDIDFreqs" "False"
    Option         "ExactModeTimingsDVI" "True"
    Option         "Coolbits" "4"
    Option         "Stereo" "0"
    Option         "metamodes" "HDMI-0: nvidia-auto-select +2560+840, DVI-D-0: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    Modes        "1920x1080"
    EndSubSection
EndSection

```

And the EDID information from Windows

```
Monitor  Model name............... Acer P215H
  Windows description...... Generic PnP Monitor
  Manufacturer............. Acer
  Plug and Play ID......... ACR00F0
  Serial number............ LHR080064264
  Manufacture date......... 2010, ISO week 15
  Filter driver............ None
  -------------------------
  EDID revision............ 1.3
  Input signal type........ Digital
  Color bit depth.......... Undefined
  Display type............. RGB color
  Screen size.............. 480 x 270 mm (21.7 in)
  Power management......... Active off/sleep
  Extension blocs.......... None
  -------------------------
  DDC/CI................... n/a


Color characteristics
  Default color space...... sRGB
  Display gamma............ 2.20
  Red chromaticity......... Rx 0.644 - Ry 0.348
  Green chromaticity....... Gx 0.286 - Gy 0.603
  Blue chromaticity........ Bx 0.143 - By 0.070
  White point (default).... Wx 0.313 - Wy 0.329
  Additional descriptors... None


Timing characteristics
  Horizontal scan range.... 30-82kHz
  Vertical scan range...... 56-76Hz
  Video bandwidth.......... 160MHz
  CVT standard............. Not supported
  GTF standard............. Not supported
  Additional descriptors... None
  Preferred timing......... Yes
  Native/preferred timing.. 1920x1080p at 60Hz (16:9)
    Modeline............... "1920x1080" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync


Standard timings supported
     720 x  400p at  70Hz - IBM VGA
     640 x  480p at  60Hz - IBM VGA
     640 x  480p at  67Hz - Apple Mac II
     640 x  480p at  72Hz - VESA
     640 x  480p at  75Hz - VESA
     800 x  600p at  56Hz - VESA
     800 x  600p at  60Hz - VESA
     800 x  600p at  72Hz - VESA
     800 x  600p at  75Hz - VESA
     832 x  624p at  75Hz - Apple Mac II
    1024 x  768p at  60Hz - VESA
    1024 x  768p at  70Hz - VESA
    1024 x  768p at  75Hz - VESA
    1280 x 1024p at  75Hz - VESA
    1152 x  870p at  75Hz - Apple Mac II
    1280 x  720p at  60Hz - VESA STD
    1280 x  960p at  60Hz - VESA STD
    1152 x  864p at  75Hz - VESA STD
    1280 x 1024p at  60Hz - VESA STD
    1280 x  800p at  60Hz - VESA STD


Report information
  Date generated........... 2014-10-18
  Software revision........ 2.90.0.1000
  Data source.............. Registry-Active
  Operating system......... 6.2.9200.2


Raw data
  00,FF,FF,FF,FF,FF,FF,00,04,72,F0,00,95,7E,50,01,0F,14,01,03,80,30,1B,78,2E,C5,85,A4,59,49,9A,24,
  12,50,54,BF,EF,80,81,C0,81,40,71,4F,81,80,81,00,01,01,01,01,01,01,02,3A,80,18,71,38,2D,40,58,2C,
  45,00,DC,0C,11,00,00,1E,00,00,00,FD,00,38,4C,1E,52,10,00,0A,20,20,20,20,20,20,00,00,00,FF,00,4C,
  48,52,30,38,30,30,36,34,32,36,34,0A,00,00,00,FC,00,41,63,65,72,20,50,32,31,35,48,0A,20,20,00,C5
```

---

### Post by d.maarouf on 2014-10-19
Marked as solved. When I had the single 2560x1440 monitor connected I told xorg to just force 2560x1440 and not look for an EDID because the EDID was corrupted for that monitor. This is the reason why the new second monitor was not detecting correctly. I made an EDID binary for the 1440p monitor and told xorg to use it. Both monitors are working perfectly now. Here is a download for the Shimian QH270 EDID if anyone needs it, it apparently works with some of the other Korean 1440p monitors.

[http://www78.zippyshare.com/v/41839817/file.html](http://www78.zippyshare.com/v/41839817/file.html)

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig# nvidia-xconfig:  version 343.22  (buildmeister@swio-display-x86-rhel47-05)  Thu Sep 11 16:49:51 PDT 2014




Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Shimian"
    ModelName      "QHD270"
    HorizSync      88.8
    VertRefresh    59.5
    Option         "DPMS"
    Modeline       "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
    DisplaySize    597 336  
EndSection


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Acer"
    ModelName      "Acer P215H"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 780"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-3"
    Option         "nvidiaXineramaInfoOrder" "DFP-3"
    Option         "ExactModeTimingsDVI" "True"
    Option         "metamodes" "DVI-I-1: nvidia-auto-select +2560+360, DVI-D-0: nvidia-auto-select +0+0"
    Option         "CustomEDID" "DFP-3:/path/to/shimian_edid.bin; DFP=0:/path/to/asus_edid.bin"
    Option         "ConnectedMonitor" "Monitor0, Monitor1"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

---

