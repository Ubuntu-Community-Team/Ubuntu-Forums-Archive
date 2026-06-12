---
title: "freedesktop-compiz and xorg.conf"
date: 2006-10-31
forum: General Help
---

### Post by Bou on 2006-10-31
Hi, I just tried installing freedesktop-compiz ([http://gandalfn.wordpress.com/)](http://gandalfn.wordpress.com/)), so I added the repos and modified my xorg.conf according to this faq: [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy)

Even so, when I launch the preference manager I get this error message:

[[IMG]http://img248.imageshack.us/img248/9418/pantallazognomecompizprgm4.th.png[/IMG]](http://img248.imageshack.us/my.php?image=pantallazognomecompizprgm4.png)

Compiz, however, seems to work, but sometimes I get low performance. What's the matter with xorg and compiz?

This is my xorg:

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice	   "Synaptics Touchpad"
    Option         "AIGLX" "true"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dri"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
Load "bitmap"
Load "ddc"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29,0 - 50,0
    VertRefresh     0,0 - 60,0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
    Option         "XAANoOffscreenPixmaps"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP: 1280x800 +0+0, TV: nvidia-auto-select +128+16"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "true"
    Option       "CircularScrolling" "1"
    Option       "CircScrollDelta" "0.1"
    Option       "CircScrollTrigger" "3"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


---

### Post by tuxcantfly on 2006-11-06
[http://ubuntuforums.org/showthread.php?t=263840&highlight=compiz+official](http://ubuntuforums.org/showthread.php?t=263840&highlight=compiz+official)

should help, you will need the beta nvidia drivers

---

