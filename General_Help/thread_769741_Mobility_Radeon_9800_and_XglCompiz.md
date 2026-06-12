---
title: "Mobility Radeon 9800 and Xgl/Compiz"
date: 2008-04-26
forum: General Help
---

### Post by Lithia on 2008-04-26
So, I just made the upgrade to Kubuntu 8.04 and have been pleased (except a few issues like my bluetooth mouse and keyboard, which I am still working on).  But I have decided I would really like to get compiz working this time around.  I believe I have the hardware capable of its features (Dell XPS Gen 1 Extreme Edition, with a Mobility Radeon 9800 with 256 MB of Ram.)  I  have never managed it yet.

First, I have tried several things.  The bottom line is this: Right now, I have the fglrx drivers working correctly with the output of fglrxinfo looking like: 
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9800
OpenGL version string: 2.1.7412 Release
```

However, xserver-xgl was not installed by default.  When I install it, it seems to revert back to the Mesa drivers for some reason.  (It also takes forever to do anything, as the CPU is trying to run the Xgl commands,)  So, I uninstalled and it went back the the output above.

How do I get my Xgl to work without it reverting to the Mesa drivers?  Any ideas?

Thanks in advance.  Also, here is my xorg.conf, in case anyone is interested.

```
Section "Files"
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
        Identifier      "MX1000"
        Driver          "evdev"
        Option          "Name"  "Logitech MX1000 mouse"
        Option          "Phys"  "00:07:61:3A:31:77"

EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc M18 JN [Radeon Mobility 9800]"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "fglrx"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M18 JN [Radeon Mobility 9800]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1920x1200"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "MX1000"        "SendCoreEvents"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
        Load            "dbe"
        Load            "v4l"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
Section "device" #
        Identifier      "device1"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "fglrx"
        Screen  1
EndSection
Section "screen" #
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" #
        Identifier      "monitor1"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
```

---

