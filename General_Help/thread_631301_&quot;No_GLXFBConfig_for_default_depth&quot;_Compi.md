---
title: "&quot;No GLXFBConfig for default depth&quot; Compiz and Dual Monitors"
date: 2007-12-04
forum: General Help
---

### Post by matthen on 2007-12-04
Hey Everyone and thank you for any help.

I'm using Gutsy on my laptop, and had Compiz-Fusion running perfectly. Then I decided to try to set it up with an external monitor. I managed to do that, but it no longer works with compiz. It uses xinerama currently so I can drag windows from one monitor to another.

I'm using the i810 driver for an integrated graphics card in my Compaq nx7400, below is what I get when I try to launch compiz:

```

:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1568) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
**/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.**
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

Below is my current xorg.conf :
```

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/X11R6/lib/X11/fonts/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/X11R6/lib/X11/fonts/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/X11R6/lib/X11/fonts/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
 Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "Device"
Identifier "Intel0"
Driver "i810"
Option "VBERestore" "yes"
Option "MonitorLayout" "CRT,LFP"
BusID "PCI:0:2:0"
Option "AGPMode" "4"
Screen 0
EndSection

Section "Device"
Identifier "Intel1"
Driver "i810"
Option "VBERestore" "no"
Option "MonitorLayout" "CRT,LFP"
Option "DevicePresence" "yes"
BusID "PCI:0:2:0"
Option "AGPMode" "4"
Screen 1
EndSection

Section "Monitor"
Identifier "LCD"
HorizSync 28-64
VertRefresh 43-60
Option "DPMS"
EndSection

Section "Monitor"
Identifier "External Monitor"
HorizSync 31-64
VertRefresh 56-75
Option "DPMS"
EndSection

Section "Screen"
Identifier "LCD"
Device "Intel0"
Monitor "LCD"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "VGA"
Device "Intel1"
Monitor "External Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "LCD"
Screen 1 "VGA" Above "LCD"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
Option "Xinerama" "true"
EndSection

 Section "DRI"
 Mode 0666
 EndSection

```

I'd really appreciate any help/pointers-

Thanks,

Matt

---

