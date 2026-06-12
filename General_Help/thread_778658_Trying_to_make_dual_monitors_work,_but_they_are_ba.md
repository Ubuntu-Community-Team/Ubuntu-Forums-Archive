---
title: "Trying to make dual monitors work, but they are backwards..?"
date: 2008-05-02
forum: General Help
---

### Post by mortexic on 2008-05-02
What I've got:
Ubuntu 8.04 fresh n clean.
NV GeForce 6600 using the nvidia binary driver
2 monitors, one is 1440x900 widescreen (DVI), the other is 1280x1024 (VGA)

I want to use the widescreen monitor as the "primary" display.

I've currently got both monitors working at the correct resolution, and my desktop expands between both monitors perfectly. The problem is that the 1280x1024 monitor is the "primary" screen (where the ubuntu menu appears, etc) and despite some tweaking xorg.conf I cant seem to make it work correctly. I'm non-noob but have no experience with dual monitors. 

I tried using the guiconfig tool, and it got me this far, but attempting to switch the "primary" display with it gets some bizzare results. :???:

Here is my xorg.conf

```
Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" leftof "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "int10"
        Load            "vbe"
        Load            "glx"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x1024"
        Horizsync       31.5-64.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Gamma   1.0
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Boardname       "nvidia"
        Busid           "PCI:5:0:0"
        Driver          "nvidia"
        Screen  1
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "NoLogo"        "True"
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection

Section "device" #
        Identifier      "device1"
        Boardname       "nvidia"
        Busid           "PCI:5:0:0"
        Driver          "nvidia"
        Screen  0
EndSection
Section "screen" #
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Virtual 1440    900
                Modes           "1440x900@60"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "800x600@56"
        EndSubSection
EndSection
Section "monitor" #
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1440x900"
        Horizsync       31.5-56.0
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
        Gamma   1.0
EndSection
Section "ServerFlags"
        Option          "Xinerama"      "true"
EndSection

```


Thoughts?


Another semi-related(?) question, 
When I get this working as-described with the widescreen monitor as the "primary", how does/will xorg handle it when a game (wow via wine, wesnoth, flightgear, whatever) changes to "fullscreen" mode?

Thanks!

---

### Post by cammin on 2008-05-03
Change
```
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" leftof "Default Screen"
```

to
```
  screen 0 "screen1" 0 0
  screen 1 "Default Screen" leftof "screen1"
```

in the **Server Layout** section.

You can change **leftof** to **rightof** or **relative**
If you use **relative**, you have to add the starting coordinates to the end so it would look like

```
screen 1 "Default Screen" relative "screen1" 1440 0
```

---

