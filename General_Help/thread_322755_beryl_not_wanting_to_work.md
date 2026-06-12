---
title: "beryl not wanting to work?"
date: 2006-12-20
forum: General Help
---

### Post by squidmaster on 2006-12-20
```
ika@ika-ubuntu2:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
ika@ika-ubuntu2:~$ beryl-manager
ika@ika-ubuntu2:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

when I try to run it....

Other info
**fglrxinfo**
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1
```

**specs**
CPU: AMD A64 3500+ Venice
GPU: ATi x800GTO 256/256 PCI-e
INST: Ubuntu 6.10/Edgy

---

### Post by K.Mandla on 2006-12-21
I'm not an ATI expert, so I'm going to ask what might be a newbish question first ... did you install the proprietary ATI drivers?

This might be of use: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by squidmaster on 2006-12-21
> **K.Mandla said:**
> I'm not an ATI expert, so I'm going to ask what might be a newbish question first ... did you install the proprietary ATI drivers?

This might be of use: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

yeah I did install the fglrx drivers correctly and they are working.
I will do it again just to make sure.
Have to get back to you on this later tonight as I am at work right now

---

### Post by arron on 2006-12-21
mesa is the generic drivers, and don't support 3d.  Your fglrx info should look something similar to:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

With ATI driver running, not mesa.  Here is a link to help set it up, by following the link below (as posted before), it should come up for u,

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

or this may shed some light

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

as well a script called "ati-8.32.5-builder.sh" that i found on this forum did it all, u can do a search for that name and it should get a few hits, here is the script (but do a search to get more help/info):

```

#!/bin/bash
apt-get update
apt-get install module-assistant build-essential wget
apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run
chmod +x ati-driver-installer-8.32.5-x86.x86_64.run
./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/dapper
dpkg -i xorg-driver-fglrx_8.32.5-1_i386.deb fglrx-kernel-source_8.32.5-1_i386.deb fglrx-control_8.32.5-1_i386.deb
rm /usr/src/fglrx-kernel*.deb
module-assistant prepare
module-assistant update
module-assistant build fglrx
module-assistant install fglrx
depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv
```

as well you may, or may not need to add this to your /etc/X11/xorg.conf file (from what i understand most of the new ati drivers dont support dri-composite, but some do), this will disable it:

#fglrx support
Section "Extensions"
Option "Composite" "0"
EndSection

You can do a search on some of those keywords for more info if you still need help.

This worked no problem for me, after i had SEVERAL problems getting my ATI card to work.  When they are installed, you will see ati drivers for the fglrxinfo screen, and if you run fgl_glxgears you will see gears turning ins a box thats rotating.

hope this helps, search more on here, there is TONNES of posts about ati problems....  I don't think i will buy ati again.

---

### Post by squidmaster on 2006-12-21
Oh wow great thanks a lot.
I will test this out as soon as I get home from work.

---

### Post by squidmaster on 2006-12-21
ok
so
reinstalled the fglrx
and it works the right way now (the drivers)
but beryl still wont

```
ika@ika-ubuntu2:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension

```

---

### Post by squidmaster on 2006-12-21
bump....

---

### Post by squidmaster on 2006-12-22
```
ika@ika-ubuntu2:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.6011 (8.28.8)

ika@ika-ubuntu2:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension

```

hmmph

xorg.conf file
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL E152FP"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Driver      "fglrx"
	Option	    "TripleBuffer" "true"
	Option	    "ColorTiling" "on"
	Option	    "EnablePageFlip" "true"
	Option	    "AccelMethod" "EXA"
	Option	    "XAANoOffScreenPixMaps"
	Option	    "RenderAccel" "true"
	Option	    "DRI" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Monitor    "DELL E152FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"

# Enable 32-bit ARGB GLX Visuals
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
#    Option "DisableGLXRootClipping" "True"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
		Option	    "AddARGBGLXVisuals" "True"
# If you are using an older version of compiz that
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "enable"
EndSection


```

---

### Post by Martey on 2007-01-03
> XGL Absent, checking for NVIDIA

This may seem like a stupid question, but did you install XGL (xserver-xgl)?

---

