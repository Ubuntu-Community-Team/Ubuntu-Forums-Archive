---
title: "ubuntu  help"
date: 2007-11-23
forum: General Help
---

### Post by hackattack on 2007-11-23
my computer is  a dell optiplex Gx150 , Ubuntu is intalled on it , my problem is that my monitor  have some line showing up every second on the screen.  does any one know  what is the cause of this.?

is it a driver prob?

help please!  what am to do ?

---

### Post by jfinkels on 2007-11-23
What kind of video card do you have? What is the output of typing the following command in the terminal:```
cat /etc/X11/xorg.conf
```

---

### Post by hackattack on 2007-11-23
> **jfinkels said:**
> What kind of video card do you have? What is the output of typing the following command in the terminal:```
cat /etc/X11/xorg.conf
```

hold on let me try that and see. ok

---

### Post by hackattack on 2007-11-23
THIS  is what I get



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
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "IBM E74"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
        Monitor         "IBM E74"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

---

### Post by hackattack on 2007-11-23
jfinkels   here is the info


Section "Device"
Identifier "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "IBM E74"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
Monitor "IBM E74"
DefaultDepth 24
SubSection "Display"
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection



what must i do know?

---

### Post by jfinkels on 2007-11-23
Okay, you are using integrated Intel video. Search using Google and search on the forums to see if anyone else has had any problems with your Intel chipset (or your specific make and model of computer) and if there are any solutions.

To see the kind of video card you have, type the following in the terminal:```
sudo lspci -v
```and look for a line that looks like this:```
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300] (prog-if 00 [VGA])
``` That happens to be my video card, yours will look different.

---

### Post by hackattack on 2007-11-23
> **jfinkels said:**
> Okay, you are using integrated Intel video. Search using Google and search on the forums to see if anyone else has had any problems with your Intel chipset (or your specific make and model of computer) and if there are any solutions.

To see the kind of video card you have, type the following in the terminal:```
sudo lspci -v
```and look for a line that looks like this:```
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300] (prog-if 00 [VGA])
``` That happens to be my video card, yours will look different.

this what i get 

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04) (prog-if 00 [VGA])

---

### Post by hackattack on 2007-11-24
i solve my problem

thanks for your help

---

