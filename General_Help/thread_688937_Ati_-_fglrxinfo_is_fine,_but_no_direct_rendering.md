---
title: "Ati - fglrxinfo is fine, but no direct rendering"
date: 2008-02-05
forum: General Help
---

### Post by glisignoli on 2008-02-05
So, I followed this guide: [Ubuntu Gutsy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
All went well, when I run fglrxinfo I get:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7276 Release

```
Good!
But when I run glxinfo | grep direct I get:
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

Any ideas how I can enable direct rendering? Here is my xorg file:
```

# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"

 # 
	Identifier   "monitor1"
	VendorName   "Generic CRT Display"
	ModelName    "Monitor 1600x1200"
	HorizSync    31.5 - 107.5
	VertRefresh  50.0 - 85.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Monitor"

 # 
	Identifier   "monitor2"
	Gamma        1
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

 # 
	Identifier  "device1"
	Driver      "vesa"
	BoardName   "VESA driver (generic)"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"

 # 
	Identifier  "device2"
	Driver      "vesa"
	BoardName   "VESA driver (generic)"
	BusID       "PCI:1:0:1"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"

 # 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1600x1200@60" "1600x1200@75" "1600x1200@65" "1600x1200@70" "1400x1050@75" "1600x1200@85" "1400x1050@60" "1792x1344@75" "1280x960@75" "1792x1344@60" "1280x1024@60" "1856x1392@60" "1280x1024@85" "1920x1440@60" "1280x960@85" "2048x1536@60" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
	EndSubSection
EndSection

Section "Screen"

 # 
	Identifier "screen2"
	Device     "device2"
	Monitor    "monitor2"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

---

### Post by keenboy on 2008-02-06
Looks as if you have 3 devices specified 2 of which are using the vesa drivers, the device with the fglrx driver seems ok. would it be worth commenting out the others if they're not needed?

Also a good 'non free' graphics driver install tool and xorg configurator is called envy

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I used it to configure my ATI card, it may help you!

---

### Post by jamespickles on 2008-02-06
```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```

change that to:
```
Section "Extensions"
        Option      "Composite" "1"
EndSection
```

and download and install the xserver-org file - cant remember full name but its something liike that, then restart after that, worked for me.

---

### Post by glisignoli on 2008-02-06
Here is my new xorg.conf file. Still no direct rendering.
```

# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "dri"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection



Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

After looking around google, I found this [page.](http://dri.freedesktop.org/wiki/DriTroubleshooting)
It mentions: > DRM
Check that the DRM (Direct Rendering Module, the kernel module) is loaded and has found your card. Do dmesg | grep drm. You should have several lines of info, with samples below:

Well nothing shows up, so I assume that the Direct Rendering Module isn't loaded in the kernel. Any idea how I can add or verify this?

---

### Post by nlz on 2008-03-02
i am having the same problem. i'm going to install envy  now. i'll report back when i'm finished..

---

### Post by nlz on 2008-03-21
envy didn't work it couldn't find the appropriate driver or couldn't come through the proxy, so i downloaded ati-driver-installer-8-02-x86.x86_64.run  and installed it, but now everything is really slow and i still dont have direct rendering.

Just found out that Ati's got a new driver for my card (at radeon mobility x1600) (ati-driver-installer-8-3-x86.x86_64.run). I'll just try to install that to see what happens..

Now i got a ATI catalyst option in my menu, but it doesn't work. thanks ati. 

envy wants me to choose between driver that are quite old (the newest is from november 2007)..

---

### Post by justleen on 2008-03-21
> **nlz said:**
> envy didn't work it couldn't find the appropriate driver or couldn't come through the proxy, so i downloaded ati-driver-installer-8-02-x86.x86_64.run  and installed it, but now everything is really slow and i still dont have direct rendering.

Just found out that Ati's got a new driver for my card (at radeon mobility x1600) (ati-driver-installer-8-3-x86.x86_64.run). I'll just try to install that to see what happens..

Now i got a ATI catalyst option in my menu, but it doesn't work. thanks ati. 

envy wants me to choose between driver that are quite old (the newest is from november 2007)..

Trying to install driver over driver isbt a good idea with ATi :)
Make sure you :
- backup your xorg.conf
- run a dpkg-reconfigure xserver-xorg to "reset" xorg to default


i got an ATi radeon X1600 Mobile too. this worked flawlessly for me (sinle monitor!):

sudo apt-get install dpkg-dev debhelper libstdc++5 dkms

./ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/Ubuntu7.10
sudo dpkg -i fglrx-kernel-source_<version>.deb
r
sudo dpkg -i xorg-driver-fglrx_<version>.deb
:
sudo aticonfig --initial

---

### Post by nlz on 2008-03-22
hi leen,

You're right, i had to reinstall last night due to driver on driver... pfwuh...
Are you sure that direct rendering is working with you? ( just check at glxinfo )

If so, i will do it, but my co-worker will kill me if i mess-up the computer for half a day again...

i followed this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) but it didn't work..

---

### Post by nlz on 2008-03-24
direct rendering is working without XGL, but when i install XGL, it goes back to MESA => no direct rendering.

So now I uninstalled XGL again, but now i get a menu when i start up: gnome setting for keyboard are different then x windows setting. Where are these setting saved so i disable this?

I thought i read it was possible to get compiz working without XGL, but i cannot find it anymore...

---

