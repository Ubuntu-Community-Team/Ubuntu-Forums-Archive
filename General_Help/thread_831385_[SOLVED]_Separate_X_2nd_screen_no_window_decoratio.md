---
title: "[SOLVED] Separate X 2nd screen no window decoration"
date: 2008-06-16
forum: General Help
---

### Post by ktechman on 2008-06-16
I have been working with Twinview for some weeks now but have recently discovered that the applications I need to work with, namely Impress and Lyricue work best on a Separate X configuration. Separate X is working but the window boarder on the second screen is missing I have the 
```
 Option  "AddARGBGLXVisuals"  "True" 
```

In the "Device" section and the "Screen" section

My xorg.conf file is as follows
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    
    Load           "glx"
    
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor 2"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "VIZ VW26L HDTV10F"
    HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 85.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation  G70 [GeForce 7600GS]"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GS] 2"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70  [GeForce 7600 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "720x400" "640x480"
        Option         "AddARGBGLXVisuals" "True"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen 2"
    Device         "nVidia Corporation G70 [GeForce 7600 GS] 2"
    Monitor        "Generic Monitor 2"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1360x768" "1024x768" "800x600" "720x400" "640x480"
        Option         "AddARGBGLXVisuals" "True"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1440x900 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
     Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

``` 

I could really use some input on this one.  Thank you in advance:)

---

### Post by ktechman on 2008-06-17
As soon as I turn "Compiz" off all of the second screen issues are repaired.

What is the problem with compiz???????

---

