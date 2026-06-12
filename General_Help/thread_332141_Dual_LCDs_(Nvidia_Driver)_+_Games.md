---
title: "Dual LCDs (Nvidia Driver) + Games?"
date: 2007-01-05
forum: General Help
---

### Post by ykram on 2007-01-05
I currently have my dual LCDs working nicely with the binary Nvidia drivers. I'm using twinview in my xorg.conf but I'm having problems playing some Quake games. In quake 4, the screen spans across both LCDs which is just annoying. When I play quake 3, there's no problem really except for when I lower the resolution from 1280x1024 (my native resolution) to something lower, in which case the entire background is black and quake 3 is minimized to 800x600 (for example) to the bottom left portion of the screen. 

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
    FontPath        "/usr/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/misc/"
    FontPath        "/usr/lib/X11/fonts/Type1/"
    FontPath        "/usr/lib/X11/fonts/100dpi/"
    FontPath        "/usr/lib/X11/fonts/75dpi/"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver        "evdev"
    Option        "CorePointer"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-0000:00:10.2-1/input0"
    Option        "Device"          "/dev/input/event9"
    Option        "Buttons"         "10"
    Option        "ZAxisMapping"    "4 5"
#    Option       "ButtonMapping"   "1 2 3 6 7"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
EndSection

#Section "InputDevice"
#    Identifier         "Keyboard0"
#    Driver     "evdev"
    Option        "CorePointer"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-0000:00:10.2-1/input0"
    Option        "Device"          "/dev/input/event9"
    Option        "Buttons"         "10"
    Option        "ZAxisMapping"    "4 5"
#    Option       "ButtonMapping"   "1 2 3 6 7"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
EndSection

#Section "InputDevice"
#    Identifier         "Keyboard0"
#    Driver     "evdev"
#    Option     "Dev Phys"          "usb-0000:00:10.2-2/input4"
#    Option     "Device"            "/dev/input/event0"
#    Option     "CoreKeyboard"
#EndSection

Section "Monitor"
    # HorizSync source: option, VertRefresh source: option
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview LCD 17S"
    Option         "HorizSync" "30-85"
    Option         "VertRefresh" "50-160"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GS/XT"
    Option         "SecondMonitorHorizSync" "31.4-68.6"
    Option         "SecondMonitorVertRefresh" "59-75"
    Option         "RenderAccel" "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024_75 +0+0, CRT-1: 1280x1024_75 +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by ykram on 2007-01-05
Okay nevermind :D I figured it out.

---

### Post by nwillis on 2007-04-26
ykram,
Please post the solution that you found -- there may be other people who experience the same problem, and by following up on it, you can help them out a great deal.

---

### Post by palermi on 2007-05-01
you need configure the metamodes

example:

you have 2 monitors in 1280x1024 and 1280x1024

And you wish run a game in fullscreen (in the resolution 800x600). In this case you need this metamode 800x600,NULL
if you wish run a game in the resolution 640x480 you need 640x480,NULL

In both cases when you run the games, in the first monitor appear the game, and the another monitor will poweroff

If you run games in 1024x1024 i dont know

Sorry for my poooooooor english

---

