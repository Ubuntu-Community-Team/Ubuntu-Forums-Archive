---
title: "Multiseat issues"
date: 2013-05-19
forum: General Help
---

### Post by malaTG on 2013-05-19
Hi everyone,

I am trying to get a multiseat setup to work in 12.04 but are having issues getting it to work. Here are my configuration files

xorg.conf

```
#My own Xorg file

Section "ServerFlags"
    Option         "DefaultServerLayout" "seat0"
    Option         "AllowMouseOpenFail"  "true"
    Option         "AutoAddDevices"      "false"
    Option         "AutoEnableDevices"   "false"
    Option         "DontZap"             "false"
EndSection

Section "ServerLayout"
    Identifier     "seat0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier     "seat1"
    Screen      0  "Screen1" 0 0
    InputDevice    "Mouse1" "CorePointer"
    InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard1"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.2:1.0-event-kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "evdev"
    Option         "GrabDevice" "yes"
EndSection

Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.2-usb-0:2.2:1.0-event-kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "evdev"
    Option         "GrabDevice" "yes"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse1"
EndSection


Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL U2312HM"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       15.0 - 50.0
    VertRefresh     49.0 - 71.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0; DFP-0: 1280x720 +0+0; DFP-0: 1280x720_60_0 +0+0; DFP-0: 1280x720_50 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 800x600 +0+0; DFP-0: 720x576 +0+0; DFP-0: 720x480 +0+0; DFP-0: 640x480 +0+0; DFP-0: nvidia-auto-select @1360x765 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

lightdm.conf

```
[LightDM]

minimum-display-number=0
minimum-vt=7

[SeatDefaults]
xserver-command=/usr/bin/X
greeter-session=unity-greeter
greeter-show-manual-login=true
user-session=ubuntu
exit-on-failure=true

[Seat:0]
xserver-command=/usr/bin/X :0
xserver-layout=seat0
autologin-user=mala

[Seat:1]
xserver-command=/usr/bin/X :1 -sharevts
xserver-layout=seat1


``` 

could someon help me on where to look to find the problem?

Best regards

Marcus

---

### Post by malaTG on 2013-05-25
Hi again everyone,

After reading up a bit on this I realized that I need a separate graphic card which I bought but I still can´t get it to work. Could someone help me on where I can find some more information on what might be wrong? 

here is my new xorg file, the lightdm.conf is the same

```

#My own Xorg file

Section "ServerFlags"
    Option         "DefaultServerLayout" "seat0"
    Option         "AllowMouseOpenFail"  "true"
    Option         "AutoAddDevices"      "false"
    Option         "AutoEnableDevices"   "false"
    Option         "DontZap"             "false"
EndSection

Section "ServerLayout"
    Identifier     "seat0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier     "seat1"
    Screen      0  "Screen1" 0 0
    InputDevice    "Mouse1" "CorePointer"
    InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard1"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1.2:1.0-event-kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "evdev"
    Option         "GrabDevice" "yes"
EndSection

Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-path/pci-0000:00:1d.2-usb-0:2.2:1.0-event-kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "evdev"
    Option         "GrabDevice" "yes"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse1"
EndSection


Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL U2312HM"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       15.0 - 50.0
    VertRefresh     49.0 - 71.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:8:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```


Marcus

---

### Post by pooherman on 2013-07-04
[FONT=Menlo]Section "Device" [/FONT]
[FONT=Menlo]Identifier "Device0" [/FONT]
[FONT=Menlo]Driver "radeon" [/FONT]
[FONT=Menlo]VendorName "ATI Technologies Inc" [/FONT]
[FONT=Menlo]BoardName "ATI 3100" [/FONT]
[FONT=Menlo]BusID "PCI:1:5:0" [/FONT]
[COLOR=#ff0000][FONT=Menlo]Option "Int10" "off" [/FONT][/COLOR]
[FONT=Menlo]EndSection [/FONT][URL="http://habrahabr.ru/post/112534/"]

http://habrahabr.ru/post/112534/[/URL]

---

### Post by malaTG on 2013-07-07
Display was broken...

---

