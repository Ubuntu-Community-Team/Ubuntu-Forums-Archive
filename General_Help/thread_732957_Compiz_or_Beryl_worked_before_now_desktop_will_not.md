---
title: "Compiz or Beryl worked before now desktop will not enable effects!!!!"
date: 2008-03-23
forum: General Help
---

### Post by willy111123 on 2008-03-23
Currently I have a Laptop with a 9600 ATI Radeon mobile chip. I have tried many fixes for Compiz and Beryl to work. At times I had to restore the Xorg.conf file and still nothing works. I finally got it to work, but the system became so sluggish that I knew something in the settings were not set right.

I then apt-get'd the Xorg-driver-fglrx video driver for ATI cards. This has now caused me to not be able to enable the extra effects. I do not know the true fix and tweaks for my system. Below I am posting my xorg.conf file:

Someone please help me with this.

xorg.conf file:

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
Driver "ati"
BusID "PCI:1:0:0"
Option "AllowGLXWithComposite" "true"
Option "GARTSize" "64"
Option "MergedFB" "off"
Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

Section "Module"
Load "dbe"
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-84
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1680x1050" "1440x900"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
Option "Composite" "Enable"
Option "AIGLX" "On"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

---

