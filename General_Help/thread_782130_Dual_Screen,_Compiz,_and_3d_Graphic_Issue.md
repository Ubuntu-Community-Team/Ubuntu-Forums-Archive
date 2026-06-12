---
title: "Dual Screen, Compiz, and 3d Graphic Issue"
date: 2008-05-04
forum: General Help
---

### Post by Neumy on 2008-05-04
I've been running an Ubuntu WebServer for about a year now, but with the release of 8.04 I've decided to give the desktop a try. 

I have a Dell laptop with a second monitor (ATI card) and am trying to configure the desktop with either "dual monitor" or "big desktop" with no luck.

1) I've been strictly modifying `xorg.conf` to enable all my changes; my first change was add the 2 Screens to ServerLayout: 

[PHP]        Screen          0 "aticonfig-Screen[0]" 0 0
        Screen          "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"[/PHP]

This worked perfectly but my 3D support was not working at this time.

2) Next I enabled 3D support installed Compiz - this worked perfectly, I was able to get the cool Cube rotation (very neat). Unfortunately, this killed my Dual Monitor. 

3) I jumped back in to `xorg.conf` to try to re-configure it back to the Dual Monitor setup, but Dual Monitor and Compiz seems to hate each other. 

4) Once I enabled Xinerama, it almost started working again; I actually have 2 monitors (although their backwards now - no matter how I set `xorg.conf` up) and can run my 3D games with good FPS. But Compiz is still not working and my second monitor is all screwed up.

My main laptop screen is perfect. My second screen (which is to the left of the laptop) is displayed on the right side and has the wrong resolution. Also, when I do play a game, it displays on both monitors.

I must have something wrong in my `xorg.conf` but can't figure it out. Or maybe I forgot to install a program that Compiz or Dual Monitor requires to run correctly. Here's my config if anyone can lend a hand:

[PHP]# xorg.conf (X.Org X Window System server configuration file)

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "aticonfig-Screen[0]" 0 0
        Screen          "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
        InputDevice     "Synaptics Touchpad"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama" "true"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
        Option          "DesktopSetup" "horizontal"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[1]"
        Driver          "fglrx"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[1]"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1280x1024"
        EndSubSection
EndSection

Section "Module"
        Load            "glx"
EndSection[/PHP]

---

