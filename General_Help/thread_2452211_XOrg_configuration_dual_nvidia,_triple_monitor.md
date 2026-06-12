---
title: "XOrg configuration dual nvidia, triple monitor"
date: 2020-10-18
forum: General Help
---

### Post by cd-site-manager on 2020-10-18
Hi, I’ve tried and googled a lot, but I know when I’m beat.
So I have a laptop, I could plugin a razer core in and configure more or  less to have everything working, the problem is that not everything  works at the same time.
Precisely, I don’t manage to make both my gpus work at the same time.  Which means either I have my built-in monitor working, either I have my 2  external monitors working, but I can’t find a way to make all 3 working  at the same time. And I’m out of ideas.
 This is my working eGPU version xorg :
```

Section "ServerLayout" 
    Identifier     "Layout0"
    Screen         "Screen0" 0 0
EndSection

Section "Module"
    Load           "modesetting"
    Load           "extmod"
    Load           "dbe"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce RTX 2080 SUPER"
    BusID          "PCI:61:0:0"
    Option         "AllowEmptyInitialConfiguration"
    Option         "AllowExternalGpus" "True"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro M620"
    BusID          "PCI:1:0:0"
    Option         "AllowEmptyInitialConfiguration"
    Option         "AllowExternalGpus" "True"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung LC27RG50"
    HorizSync       255.0 - 255.0
    VertRefresh     48.0 - 240.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung C24F390"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "LGD"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-6"
    Option         "metamodes" "DP-2: 1920x1080_240 +1980+0, DP-5: nvidia-auto-select +0+0, DFP-3"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0 {AllowGSYNC=Off}"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

If I replace the second line of the serverlayout :
```

Section "ServerLayout" 
     Identifier     "Layout0" 
     Screen         "Screen1"
EndSection

```
Then it uses the built-in monitor

 If I dare putting both in like this :
```

Section "ServerLayout" 
    Identifier     "Layout0" 
    Screen         "Screen0" 0 0 
    Screen         "Screen1" RightOf "Screen0" 
EndSection 

Section "ServerFlags" 
     Option         "Xinerama" "ON" 
EndSection

```

Then it tells me that Xinerama on with Composite extension enabled is  not supported and in fact > nothing works, I get black screen on  built-in, nothing on the others, but I can move my mouse around on the  built-in.
 if I disable Composite :
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0" 0 0
    Screen         "Screen1" RightOf "Screen0"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "ON"
EndSection

```

Then the login doesn’t work, crashes and tells me to log out and retry (so rude).

So I’m at this point, I really don’t know X server nor NVidia, so I’m out of ideas, please help me.

For info I have :

 - Ubuntu 20.04
 - gdm3 as display manager (but it’s the same results with lightdm)
 - Quadro M620 for internal GPU
 - GeForce RTX 2080 Super in the Razer Core (eGPU)

Thanks for any suggestions, if you need logs tell me of which tentative, I’m saving them all :D

---

### Post by cd-site-manager on 2020-10-22
bump

---

### Post by VinDSL on 2021-03-15
Looks like this unanswered thread has been abandoned, thus I'll just say...

In my experience, nVidia X server settings will only get one halfway there.

ARandR is your friend, and the second part of the equation: [https://is.gd/TND2EQ](https://is.gd/TND2EQ)

Put another way, one needs to use both nVidia X server + ARandR, in combination.

As an example, here are the working configs, on my triple monitor rig...

**/etc/X11/xorg.conf**```
# nvidia-settings: X configuration file generated by nvidia-settings

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    ModelName      "DELL U2913WM"
    HorizSync       29.0 - 94.0
    VertRefresh     49.0 - 86.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 710"
EndSection

Section "Screen"

# Removed Option "metamodes" "HDMI-0: nvidia-auto-select +640+0, VGA-0: nvidia-auto-select +1920+1080, DVI-D-0: nvidia-auto-select +0+1080"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "HDMI-0: 2560x1080_60 +640+0, VGA-0: nvidia-auto-select +1920+1200, DVI-D-0: nvidia-auto-select +0+1200"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

**/home/vindsl/.screenlayout/vindsl.sh**```
#!/bin/sh
xrandr --output VGA-1 --primary --mode 1920x1200 --pos 1920x1200 --rotate normal --output DVI-D-1 --mode 1920x1200 --pos 0x1200 --rotate normal --output HDMI-1 --mode 2560x1080 --pos 592x0 --rotate normal
```

The setup (above) allows three monitors to be divided into four displays -- 2 x 17", and 2 x 24"

Have fun!

---

