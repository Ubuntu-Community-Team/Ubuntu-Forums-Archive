---
title: "xorg configuration"
date: 2014-01-24
forum: General Help
---

### Post by bjm904 on 2014-01-24
I am setting up multiseat at my workstation and I am running into an issue. I would like multiseat, so each monitor has its own set of mouse and keyboard. I was following the tutorial [https://wiki.archlinux.org/index.php/xorg_multiseat](https://wiki.archlinux.org/index.php/xorg_multiseat) . I am using an ATI card with two outputs. I beleive my problem is with mapping the screens to those outputs. Most of the tutorials out there use two cards but I can't. I am using ATI Radeon HD. I am using fglrx driver in ubuntu 12.04 desktop. Here is my xorg.conf : ```
Section "ServerFlags"
        Option "AutoAddDevices"     "false"
        Option "AutoEnableDevices"  "false"
        Option "AllowMouseOpenFail" "on"
        Option "AllowEmptyInput" "on"
        Option "ZapWarning"         "on"
        Option "HandleSpecialKeys"  "off" # Zapping on
        Option "DRI2" "on"
        Option "Xinerama" "off"
EndSection

Section "InputDevice"
        Identifier      "keyboard0"
        Driver          "evdev"
        Option          "Device"                "/dev/input/by-id/usb-Dell_Dell_USB_Keyboard_Hub-event-kbd"
        Option "xkb_rules" "evdev"
        Option "xkb_model" "evdev"
        Option "xkb_layout" "us"
        Option "GrabDevice" "on"
EndSection

Section "InputDevice"
        Identifier      "keyboard1"
        Driver          "evdev"
        Option          "Device"                "/dev/input/by-id/usb-Logitech_Logitech_USB_Keyboard-event-kbd"
        Option "xkb_rules" "evdev"
        Option "xkb_model" "evdev"
        Option "xkb_layout" "us"
        Option "GrabDevice" "on"
EndSection

Section "InputDevice"
        Identifier      "mouse0"
        Driver          "mouse"
        Option          "Protocol"              "IMPS/2"
        Option          "Device"                "/dev/input/mouse0"
EndSection

Section "InputDevice"
        Identifier      "mouse1"
        Driver          "mouse"
        Option          "Protocol"              "IMPS/2"
        Option          "Device"                "/dev/input/mouse1"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[3]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP9" "0-DFP9"
    BusID       "PCI:3:0:0"
    Screen      0
EndSection

Section "Device"
    Identifier  "amdcccle-Device[3]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    BusID       "PCI:3:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "screen0"
    Device     "amdcccle-Device[3]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "screen1"
    Device     "amdcccle-Device[3]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Monitor"
    Identifier   "0-DFP9"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1080"
EndSection

Section "ServerLayout"
        Identifier      "seat0"
        Screen          "screen0"       0                   0
        InputDevice     "mouse0"        "CorePointer"
        InputDevice     "keyboard0"     "CoreKeyboard"
        Option "Clone" "off"
        Option "AutoAddDevices" "off"
        Option "DisableModInDev" "true"
EndSection

Section "ServerLayout"
        Identifier      "seat1"
        Screen          "screen1"       0                   0
        InputDevice     "mouse1"        "CorePointer"
        InputDevice     "keyboard1"     "CoreKeyboard"
        Option "Clone" "off"
        Option "AutoAddDevices" "off"
        Option "DisableModInDev" "true"
EndSection
```

And a generated xorg.conf that works (not multiseat) :

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[3]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP9"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1080"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[3]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP9" "0-DFP9"
    Option        "Monitor-DFP5" "0-DFP5"
    BusID       "PCI:3:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[3]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    BusID       "PCI:3:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[3]-0"
    Device     "amdcccle-Device[3]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3840 1920
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[3]-1"
    Device     "amdcccle-Device[3]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Any help would be great, i'm sure it's just a small mistake but I cannot see it. Thank you in advance.

---

### Post by oldos2er on 2014-01-26
Moved to General Help.

---

### Post by jp734 on 2014-01-26
Okay since nobody has responded yet, let's give it a shot.

So right now you have a setup with one pc, one video card, two monitors ,keyboards and mice. Correct? 
Are the two monitors working the way it should right now (meaning NOT MIRRORED)?
Are you seeing two mouse pointers? If yes, what happens if you move 1 mouse?

---

### Post by bjm904 on 2014-01-27
I do not have two mouse pointers and yes it is mirrored right now.

---

### Post by jp734 on 2014-01-27
Okay. First, lets make a backup of your generated xorg.conf file that works, then we'll reconfigure it.

Find and remove these
[COLOR="#0000FF"]Section "Device"
   Identifier  "amdcccle-Device[3]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    BusID       "PCI:3:0:0"
    Screen      1
EndSection

Section "Screen"
   Identifier "Default Screen"
   DefaultDepth     24
EndSection[/COLOR]

Then, add this to your serverlayout section :    
[COLOR="#0000FF"]
    Screen "amdcccle-Screen[3]-1" RightOf "amdcccle-Screen[3]-0"
    InputDevice "Keyboard 1" "CoreKeyboard"
    InputDevice "Keyboard 2" "SendCoreEvents"
    InputDevice "Mouse 1"    "CorePointer"
    InputDevice "Mouse 2"    "SendCoreEvents"
    Option      "BlankTime"  "5"[/COLOR]

Also, add " [COLOR="#0000FF"]Monitor   "0-DFP9"[/COLOR] " to your first screen section and "[COLOR="#0000FF"]"Monitor  "0-DFP5" [/COLOR]" on the second one. SAVE and TEST and cross your fingers LOL :-D

Are you using usb mouse? If yes, type lsusb and look for your mice. Pay close attention to the BUSID and make note of them.

---

### Post by bjm904 on 2014-01-28
Okay I followed your instructions. And ubuntu wouldn't boot. It stayed at the logo. I restored the old config. Just to be sure, we are building off whitch config I specified? The first or second?

---

### Post by jp734 on 2014-01-28
The second one. Isn't it the one that worked?
--- Look at the /var/log/Xorg.0.log file and check why it failed to startx.
--- Can you post the output of "lspci -k"?
--- Did you create the xorg.conf yourself or started it by using "amdconfig --initial" command and build from there?

---

