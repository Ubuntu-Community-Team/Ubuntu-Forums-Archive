---
title: "Beryl-manager reloads X, but no beryl?"
date: 2006-11-21
forum: General Help
---

### Post by staks on 2006-11-21
Hi guys,

Im fairly new to linux, and installed Kubuntu (edgy 64bit) the other week to see what all the hype about beryl is. I am having difficulties though, i followed the guide from [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA) with little trouble, however beryl doesnt seem to start up with the 'beryl-manager' command. Initially it did work, and i got all the funky animations and features, although since changing my monitor resolution beryl no long loads properly. The following happens when i type beryl-manager -


KDE desktop flashes off, and i relog in with my username and password
Nvidia logo appears
KDE loading screen appears and then im back into the standard KDE desktop without any beryl icon in the system tray, nor logo splash screen.

Has anyone got any ideas as to what the problem might be? Is there any way to find out what beryl is complaining about in a log file?

Here is a copy of my xorg.conf file

Thanks for your help :)

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option         "AIGLX" "true"
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
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "glx"
    Load           "v4l"
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
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic"
    ModelName      "Flat Panel 1680x1050"
    HorizSync       31.5 - 90.0
    VertRefresh     60.0 - 60.0
    Gamma           1
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
 #     
    Identifier     "monitor1"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    BusID          "PCI:5:0:0"
    Screen          0
Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Device"
 #     
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    BusID          "PCI:5:0:0"
    Screen          1
Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"
    SubSection     "Display"
        Depth       24
        Modes      "800x600@60" "1280x768@60" "1600x1024@60" "1680x1050@60" "1920x1200@60"
    EndSubSection
EndSection

Section "Screen"
 #     
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "true"
    Option         "RENDER" "true"
EndSection

---

### Post by ingo on 2006-11-22
hm, I'm certainly no beryl expert but I'd get the old xorg.conf working again, chuck beryl and reinstall.

---

