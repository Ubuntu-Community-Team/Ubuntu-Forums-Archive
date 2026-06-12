---
title: "Dual Display: Can't move curso to second display"
date: 2008-01-06
forum: General Help
---

### Post by archer282 on 2008-01-06
I'm attempting to set up dual displays on my desktop, using VGA LCD monitor, and a S-VIDEO connection to my television. I would prefer dual-display mode, which i have working with the exception i can't move my cursor over to the television, or really do anything on the desktop for the television. I've attempted to set up Clone-View as well, however every attempt at that results in X not starting, and me having to restore the original xorg.conf file. 

What I would really like to be able to do, is display the output of one of workspaces to the tv, however i can't seem to find anything about that, or even if it's possible.

Anyways, here is a little more information to help you understand my setup.

lspci *Graphics Card*
```
...
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
...
```

uname -r *Kernel Version *
```
2.6.22-14-generic
```

cat /etc/X11/xorg.conf *Xorg Configuration File*
```
...
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
        Identifier      "device[vga]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Screen          0
EndSection

Section "Device"
        Identifier      "device[svideo]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "MonitorLayout"         "TV,LFP"
        Option          "TVStandard"            "NTSC"
        Option          "TVOutFormat"           "SVIDEO"
        Option          "ConnectedMonitor"      "TV"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "monitor[lcd]"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Monitor"
        Identifier      "monitor[tv]"
        HorizSync       30-50
        VertRefresh     60
EndSection

Section "Screen"
        Identifier      "screen[lcd]"
        Device          "device[vga]"
        Monitor         "monitor[lcd]"
        Defaultdepth    24
EndSection

Section "Screen"
        Identifier      "screen[tv]"
        Device          "device[svideo]"
        Monitor         "monitor[tv]"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes   "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        Screen  0 "screen[lcd]"
        Screen  1 "screen[tv]" RightOf "screnp[lcd]"

EndSection

Section "ServerFlags"
        Option          "DefaultServerLayout" "Default Layout"
EndSection

Section "Module"
        Load            "glx"
EndSection
```


I would also like to mention that, when using this configuration file as opposed to the default one certain things seem to have a delay, for example when i open any context menu it takes a lot longer than usual for it display. it's not like i'm watching it paint or anything, it just seems to have a delay between when i click/hover and when it starts displaying... however when i use the original xorg conf file i do not see such a delay.

Thank you for you attention, and I appreciate any help you can give me in my endeavor.

---

