---
title: "Getting compiz running with ATI graphics card"
date: 2008-02-10
forum: General Help
---

### Post by AvengingAngel718 on 2008-02-10
I'm trying to set up my friend's laptop to run Compiz (I dual booted ubutnu and set everything up alright) but I can't get desktop effects to work with his ATI drivers. I installed the drivers already but when i try to open compiz it brings up an error window that says "Desktop effects could not be enabled". I already edited xorg.conf using the command sudo dpkg-reconfigure xserver-xorg and i'm all out of ideas. The only reason he wanted ubuntu was for the visual effects and i'm afraid he'll bail out on linux if i dont fix it! lol

---

### Post by Rocket2DMn on 2008-02-10
What model card is it and is he using the fglrx restricted drivers or the open source ati drivers?

---

### Post by AvengingAngel718 on 2008-02-10
It's an ATI Mobility Radeon x1400 , and i believe it's using the fglrx drivers and that i want to switch to the ATI drivers but i'm not sure how. I've also read elsewhere on the forums that compiz only works with ATI cards if you're running xglx as your x server, but i'm not sure how to do this either. Any help would be appreciated.

---

### Post by Rocket2DMn on 2008-02-10
To check which drivers you're using, post xorg.conf for us
```
cat /etc/X11/xorg.conf
```
You can also check to see if 3d acceleration is enabled by running
```
glxgears -info
```
If you are getting a good framerate, then you probably have 3d acceleration on.

---

### Post by pointone on 2008-02-10
You'll either need to install xserver-xgl or update to the latest version of the ATI proprietary driver.

For the Xgl solution, simply use the following command:

```
sudo apt-get install xserver-xgl
```

... and Compiz will be available the next time you log in.

For the updated driver solution, follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

---

### Post by AvengingAngel718 on 2008-02-11
xorg.conf reads like this:

Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Dell"
        Modelname       "Dell 1280x1024 Laptop Display Panel"
        Horizsync       31.5-90.0
        Vertrefresh     59.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@75"   "1280x960@60"  "1400x1050@60"   "1280x1024@75"  "1400x1050@75"  "1152x864@75"   "1600x1200@65" "1024x768@60"    "1600x1200@60"  "1024x768@70"   "1600x1200@70"  "1024x768@75"  "1792x1344@60"   "832x624@75"    "1856x1392@60"  "800x600@60"    "1920x1440@60" "800x600@75"     "800x600@72"    "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
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




3d acceleration is enabled

I'm going to try the xgl solution and if that doesnt work hopefuly you can see what i'm missing

---

### Post by pointone on 2008-02-11
You're not running the proprietary ATI driver at all. Either install it via the restricted drivers manager and install Xgl, or install the latest version from the ATI site (the latest version doesn't require Xgl).

---

### Post by Rocket2DMn on 2008-02-11
It looks like a dual monitor system.  You may want to disable the second monitor, [reconfigure X]("http://ubuntuforums.org/showthread.php?t=690760"), [install fglrx]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), then proceed.

---

