---
title: "Slow Gnome Graphics"
date: 2006-11-28
forum: General Help
---

### Post by Rocket Boy on 2006-11-28
I'm having trouble with Gnomes window rendering being very slow. If I resize or move a window, especially above another, I get trails. Also if I try to use a scroll bar the mouse flickers. I'm using the latest Nvidia drivers, and have them enabled(which helped a little). 

Other then that I haven't messed with much as far as Ubuntu is concerned. I've been using a Mac at work that I know isn't more powerful hardware wise and I would really like to be able to approach that level of smoothness with Gnome. What can I do?

Heres my computer by the way:
AMD Athlon 64 4000+
1gb of ram
Nvidia Geforce6600

---

### Post by Lord Illidan on 2006-11-28
Can you give us your /etc/X11/xorg.conf here?

And try typing top in a terminal to see which is the worst process in terms of cpu time.

---

### Post by Rocket Boy on 2006-11-28
As far as CPU time "Xorg" seemed to be the highest at about 1.3

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
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
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "NEC E700"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
    Option "HWCursor" "off"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "NEC E700"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Lord Illidan on 2006-11-28
Try installing the k7 kernel.

---

### Post by Rocket Boy on 2006-11-28
Alright, I'll try that.

---

### Post by Rocket Boy on 2006-11-28
Im sorry, what packages exactly do I need to be installing? I seem to have options... and don't want to get the wrong ones.

---

### Post by Lord Illidan on 2006-11-28
> **Rocket Boy said:**
> Im sorry, what packages exactly do I need to be installing? I seem to have options... and don't want to get the wrong ones.

Is your cpu dual core? If so : sudo apt-get install linux-k7-smp

if not, sudo apt-get install linux-k7

---

### Post by Rocket Boy on 2006-11-28
Should I see a new Kernel option when I restart the computer automatically - or do I have to do anything else?

---

### Post by Lord Illidan on 2006-11-28
> **Rocket Boy said:**
> Should I see a new Kernel option when I restart the computer automatically - or do I have to do anything else?

Are you using Edgy Eft or Dapper Drake?

---

### Post by Rocket Boy on 2006-11-28
Edgy

---

### Post by Lord Illidan on 2006-11-28
It should be done automatically. Tell us what goes on.

---

### Post by Rocket Boy on 2006-11-28
I installed it, but it doesn't show up on my Grub menu. I only see the

Ubuntu 6.whatever-generic

or however the standard one is.

---

