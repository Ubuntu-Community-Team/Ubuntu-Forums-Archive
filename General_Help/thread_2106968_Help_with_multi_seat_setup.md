---
title: "Help with multi seat setup"
date: 2013-01-20
forum: General Help
---

### Post by lavacano on 2013-01-20
Xinerama is throwing errors,  so I set up a multiseat config


```
Section "ServerFlags"
    Option "Xinerama" "0"
    Option "AllowMouseOpenFail" "true"
    Option "AutoAddDevices" "false"
    Option "AutoEnableDevices" "false"
    Option "DontZap" "false"
    Option "AutoAddGPU" "FALSE" 
    Option "DontVTSwitch" "FALSE"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "evdev"
    Option         "Device" "/dev/input/event2"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mouse0"
    #Option         "Emulate3Buttons" "no"
    #Option         "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  Identifier   "LeftMonitor"
EndSection

Section "Monitor"
  Identifier   "RightMonitor"
EndSection

Section "Device"
  Identifier  "LeftCard"
  Driver      "nvidia"
  BusID       "PCI:01:00:0"
EndSection

Section "Device"
  Identifier  "RightCard"
  Driver      "Intel"
  BusID       "PCI:00:02:0"
EndSection

Section "Screen"
  Identifier   "LeftScreen"
  Device       "LeftCard"
  Monitor      "LeftMonitor"
EndSection

Section "Screen"
  Identifier   "RightScreen"
  Device       "RightCard"
  Monitor      "RightMonitor"
EndSection

Section "ServerLayout"
  Identifier     "Left"
  Screen         "LeftScreen" 0 0
 InputDevice    "Keyboard0" "CoreKeyboard"
  InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerLayout"
   Identifier     "Right"
   Screen          "RightScreen" 0 0
#  InputDevice    "Keyboard0" "CoreKeyboard"
  InputDevice    "dummy" "CorePointer"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver     "void"
    Option     "Device" "/dev/input/mice"
    Option     "CorePointer"
EndSection

```

xorg with 2 seperate servers, Left and Right.   This works.  

I only have input on one screen.

I need to put on various movies on the second screen so I need very limited interaction.  I tried synergy but it complains of having the same hostname connected twice.  I know this would be 10x simpler if xinerama worked.  I guess whats noxt though?  I guess I'll try vnc.......

---

