---
title: "I hope my problem fits this forum"
date: 2008-02-10
forum: General Help
---

### Post by idankor on 2008-02-10
hello 
first of all i'm sorry for my poor english, i read over the internet so much but couldnt found a solution for my problem:

1. everytime i turn on the computer ubuntu wont start unless i type:

sudo dpgk-reconfigure -phigh xserver-xorg

and choose lower resolution

2. when i type in the terminal  

sudo nvidia-settings [cuz i want to change the horz-position and vert-position of my screen]
it tells me:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

3. everytime when i want to enable destop visual effects it tells me:

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, , etc

i enable it and after restart nothing happens, same again
so it is clear to me that my problem connected to my graphic card or his driver
i have geforce 5500 FX
i am totaly new to linux and dont know it so well
the urgent problem is problem number 1 

thanks in advacned !!!

---

### Post by danwood76 on 2008-02-10
Could you post the contents of your xorg.conf please?

in the terminal type this to dump it:
```

cat /etc/X11/xorg.conf
```

---

### Post by idankor on 2008-02-10
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
        Option          "Protocol"              "ExplorerPS/2"
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
        Identifier      "nVidia Corporation NV34 [GeForce FX 5500]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX 5500]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768" "800x600" "640x480"
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



notice that :
Section "Device"
        Identifier      "nVidia Corporation NV34 [GeForce FX 5500]"
        Driver          "nv"
        BusID           "PCI:1:

i tried to change the nv to nvidia but it keeps returning to the original
i forgot to mention that after i do the -phigh command i need to reboot

thanks again for any help

---

### Post by idankor on 2008-02-10
anyone has a solution maybe ? :{{

---

