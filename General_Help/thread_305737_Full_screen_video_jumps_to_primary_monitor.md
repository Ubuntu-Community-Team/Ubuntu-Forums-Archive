---
title: "Full screen video jumps to primary monitor"
date: 2006-11-23
forum: General Help
---

### Post by dk5151 on 2006-11-23
I use Xinerama since my displays need two different resolutions (HDTV and a normal monitor). Whenever I have a video or emulator going on the TV (secondary monitor) and set it to full screen, the video leaps to my primary monitor. Any ideas what I can do to fix this, or have it set up differently: Here is my xorg.conf with the irrelevant info taken out:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "DELL Screen" 0 0
    Screen      1  "HDTV Screen" RightOf "DELL Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "Monitor"
    Identifier     "DELL 1504FP"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "SONY HDTV"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "0 NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "DELL Screen"
    Device         "0 NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "DELL 1504FP"
    DefaultDepth    24
    Option         "MonitorLayout" "TMDS, TV"
    SubSection     "Display"
        Depth       1
        Modes      "1280x720" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x720" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x720" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x720" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x720" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x720" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "HDTV Screen"
    Device         "1 NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "SONY HDTV"
    DefaultDepth    24
    Option         "TVOutFormat" "DVI"
    Option         "TVStandard" "NTSC"
    Option         "ConnectedMonitor" "TV"
    SubSection     "Display"
        Depth       1
        Modes      "1280x720" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x720" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x720" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x720" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x720" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x720" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "false"
EndSection

---

### Post by TigerWolf on 2006-11-23
Fullscreen video will always jump to the primary monitor. There is no way to get it to go fullscreen on the secondary monitor. Only possible way would be to either change the primary monitor.

---

### Post by TigerWolf on 2006-11-23
Found this: [http://www.realtimesoft.com/multimon/faq.asp#VideoFullscreen](http://www.realtimesoft.com/multimon/faq.asp#VideoFullscreen) - is probably not your solution (as i think they are all windows) but it means there may be one for linux. 

This might also help - [http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-November/013701.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-November/013701.html)

---

### Post by dk5151 on 2006-11-23
I'll check it out. I appreciate the help.

---

