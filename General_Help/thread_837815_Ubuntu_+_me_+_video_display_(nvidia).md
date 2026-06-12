---
title: "Ubuntu + me + video display (nvidia)"
date: 2008-06-22
forum: General Help
---

### Post by JamoSmith on 2008-06-22
I was happy when 8.04 worked on my LG226LQT widescreen monitor immediately after installation (I couldn't get it to work at all with 7.10). However, when installing the latest NVidia driver I was forced to run their nvidia-xconfig script which results in ubuntu loading in low graphics mode (you know, that annoying low resolution dialog that comes up before the log in screen.) This is because, whatever is needed for xserver to use my nice monitor, is no longer in the xorg.conf that nvidia-xconfig generates.

I can rerun dk-whatever reconfigure and it results in a functioning xorg.conf. But then I can't use the nvidia control panel, which I presume is neccessary to get world of warcraft to run efficiently. (Nvidia tells me to run nvidia-xconfig, under these circumstances)

I've tried copying stuff from the nvidia xorg.conf to the working xorg.conf with no luck (like the Module section, Files section, and driver stuff). Below I pasted the two files. I hope someone can help me so I don't have to abandon Ubuntu again :(

I've also tried manually configuring the display settings after receiving the low resolution dialog, while using the xorg.conf from nvidia. I have had no luck doing this, although I have tried every combination all the way to using the exact driver off the monitor's CDROM and the correct Nvidia device driver.

If you help, thanks.

Top is the xorg.conf generated automatically by: sudo dpkg-reconfigure xserver-xorg
Bottom is the xorg.conf generated automatically by: sudo nvidia-xconfig

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


===========

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by zzantozz on 2008-06-22
Any help here?

---

