---
title: "glxgears - 1150 FPS?"
date: 2008-01-04
forum: General Help
---

### Post by ~LoKe on 2008-01-04
I realize glxgears is not a viable benchmark for FPS, but I can't help but think there's a problem.

I have an 8600GT with the latest nvidia drivers (169.07) on 64bit Gutsy Gibbon.

Without Twinview enabled, I get over 7xxx.  And long ago, with a 7900GS, I was getting over 10k.

I'm using a very minimal environment (Awesome, a fork of DWM).  No compiz, nothing complicated, no apps running.  I've also noticed that my system drags when converting avi's to mpeg using ffmpeg, and there's no good reason for it as I'm using an 8 series nvidia card with a quad core processor.  Something just doesn't seem right.

So...where should I start looking for a problem?  Here's my /etc/X11/xorg.conf:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "glx"
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
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseEdidFreqs" "True"
    Option         "DFP"
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection
```

---

### Post by markharding557 on 2008-01-04
it is quite normal for video encoding to slow a system down because it will take as much cpu time as it can.
to reduce this you would have to change the programs priority which you can do in system monitor app
click processes tab,right click relevent process and you will see 'change priority'move the slider.
doing this may make your encoding a bit slower

---

### Post by ~LoKe on 2008-01-04
It shouldn't really be that way.  ffmeg only uses 1/4 of my processing power (100% divided over four cores).  I should still have 3/4 of my power at my disposal.

---

### Post by markharding557 on 2008-01-04
i'm not sure then mate but thats one serious system!

---

