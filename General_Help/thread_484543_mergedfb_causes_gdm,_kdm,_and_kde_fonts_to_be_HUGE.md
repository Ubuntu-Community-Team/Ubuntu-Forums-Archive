---
title: "mergedfb causes gdm, kdm, and kde fonts to be HUGE (but not gnome)"
date: 2007-06-25
forum: General Help
---

### Post by harty83 on 2007-06-25
I have a mergedfb setup to get dual monitors working on my laptop with an intel 945gm graphics card.  But when I have this setup, the fonts in gdm, kdm, and even when logged into kde are HUGE.  I mean huge and not matter what the settings are, they stay the same size...HUGE.  However, it does not seem to affect gnome's fonts other than the splash screen that comes up when logging in.  Below is my xorg file.  Any clue what could be causing the huge fonts?

```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "i2c"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"

        VideoRam        131072

        Option  "DRI"                           "true"
        Option  "MergedFB"                      "true"
        Option  "MonitorLayout"                 "CRT,LFP"
        #Option "DDC"                           "false"
        Option  "VBERestore"                    "true"

        Option  "SecondPosition"                "Above"
        Option  "MetaModes"                     "1280x800-1280x1024"
        Option  "SecondMonitorHorizSync"        "31-81"
        Option  "SecondMonitorVertRefresh"      "56-76"

        #Option  "XAANoOffscreenPixmaps"         "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync 30-81
        VertRefresh 56-76
        DisplaySize 350 700
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1280x1024"
                Virtual         1280 1824
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

