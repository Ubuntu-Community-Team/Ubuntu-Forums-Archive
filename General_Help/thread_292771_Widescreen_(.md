---
title: "Widescreen? :("
date: 2006-11-04
forum: General Help
---

### Post by DAFORZE on 2006-11-04
Hey guys!
I have searched and searched but I don't know how to change my resolution to 1440 x 900.
I have installed the ati drivers and when i type: fglrxinfo
I get the correct information:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)

I found that i have to do something with modeline in xorg.conf but after a lot of search i still don't know how.](*,) 
This is my monitor specs:
    * Max H-Sync Rate   * 80 kHz 
    * Max Resolution    * 1440 x 900 
    * Max V-Sync Rate   * 75 Hz 

Thnx for any reply!

---

### Post by Kateikyoushi on 2006-11-04
Did you add the resolution to your /etc/X11/xorg.conf ?

---

### Post by DAFORZE on 2006-11-04
I putted the resolution in:

SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

But that doesn't work :(

**Below is a section of my xorg.conf:**

Section "Monitor"
	Identifier   "PLE1900WS"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "PLE1900WS"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
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

---

### Post by dbott67 on 2006-11-04
Try adding the following line:

```
Section "Monitor"
    Identifier     "PLE1900WS"
    [COLOR="Red"]VertRefresh     75.0 - 75.0[/COLOR]
    Option         "DPMS"
EndSection
```

-Dave

---

### Post by DAFORZE on 2006-11-04
Thx for you're reply, 
I tried that and restarted x but i still can't choose 1440 x 900 :(

---

### Post by dbott67 on 2006-11-04
Try this thread:

[http://ubuntuforums.org/showthread.php?p=1528132](http://ubuntuforums.org/showthread.php?p=1528132)

---

### Post by princemackenzie on 2006-11-04
> **DAFORZE said:**
> Thx for you're reply, 
I tried that and restarted x but i still can't choose 1440 x 900 :(

What you are looking for is here:

[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

Look at "getting the right mode for an LCD monitor".

A little different than the usual xorg.conf but works PERFECTLY.  Solved my problem with my 1680x1050 monitor.  If you have any more questions, let us know.

---

### Post by DAFORZE on 2006-11-04
That worked!! thx princemackenzie :D :D :D

---

### Post by princemackenzie on 2006-11-04
> **DAFORZE said:**
> That worked!! thx princemackenzie :D :D :D

You're welcome.  I had a lot of trouble with this so I do what I can to help people out with their widescreen issues :)

---

### Post by testbenchdude on 2006-12-26
Ok I am now trying to do this for my new widescreen but the link is dead... please do you have an updated link? thx

---

### Post by DAFORZE on 2006-12-26
From the google cache:

[http://209.85.135.104/search?q=cache:TQuyf_DFr34J:https://wiki.caosity.org/tiki-index.php%3Fpage%3DX%2520Server%2520Configuration+https://wiki.caosity.org+widescreen&hl=nl&gl=nl&ct=clnk&cd=1&client=firefox-a]("http://209.85.135.104/search?q=cache:TQuyf_DFr34J:https://wiki.caosity.org/tiki-index.php%3Fpage%3DX%2520Server%2520Configuration+https://wiki.caosity.org+widescreen&hl=nl&gl=nl&ct=clnk&cd=1&client=firefox-a")

:)

---

### Post by dbott67 on 2006-12-26
Just in case the cached link dies...
> **_Initial X Configuration_**

The version of Xorg-X11 that comes with cAos-2 has the capabilities to run without a configuration file. It will probe to try and find the best configuration. If this does not work, the problem is usually associated with not being able to probe the monitor or the video card is not supported. If the problem is with the monitor configuration (resolution and/or refresh rates) or you wish to change some of the default configurations, you can create your own config file. This may be done in following manner:

- Install the xorg-x11-config package by the command: **yum install xorg-x11-config**

- Menu based X configuration is started up by the command: **xorgconfig**

- Graphically X configuration is started up by the command: **xorgcfg**

This will create an xorg.config or xorg.conf file in your home directory (eg. /root/xorg.config.example). You will need to copy or move that to /etc/X11/xorg.config to activate it.

To activate some signs of a non-US keybord as well as the mouse's scroll function should the xorg.config file be edited in following way (use your favorite editor):

**_Core keyboard's InputDevice section_**

    ```
Option "XkbRules"   "xorg"
    Option "XkbModel"   "pc105"
    Option "XkbLayout"  "se"                (in this example a Swedish keyboard)
    Option "XkbVariant" "nodeadkeys"  (this script activates the signs)
```

**_Core Pointer's InputDevice section_**

    ```
Identifier  "Mouse1"
    Driver      "mouse"
    Option "Protocol" "IMPS/2"       (this script activates the scroll)
    Option "Device"      "/dev/mice"
    Option "ZAxisMapping" "4 5"    (this script activates the scroll)^
```

Now you should be able to start your x-window manager with the command: startx

**_Getting the Right Mode for an LCD monitor_**

You may have a monitor designed for a specific mode that isn't available to X under normal conditions. A widescreen LCD like the Envision H193wk is a specific example. This monitor has a native resolution of 1440x900 at 60Hz. The LCD emulates other resolutions, but these other resolutions are often unsquare, "fuzzy," or go offscreen as the monitor attempts to "fit" the image to the display area. The 1440x900@60Hz mode isn't part of the standard set of VESA modes, and may not be included in the "legal" modes returned by the video driver for your graphics card.

To add the mode to the "known" set of modes, it is necessary to define the mode for X. This is accomplished by adding a Modeline statement to the "Monitor" section of your xorg.conf file. The Modeline contains a number of specifications beyond just resolution and vertical refresh rate. An easy way of generating a full Modeline statement is to use the gtf command.

**_Using the gtf Command_**

The gtf command outputs a ready-to-use Modeline statement for your monitor given the input of resolution and vertical refresh rate of your monitor. To create the correct information for the Modeline statement, look at your monitor's manual and determine its exact native resolution and precise vertical refresh rate for that resolution. For the Envision H193wk, it is listed as 1440 by 900 at 60Hz.

Plug these values into the gtf invocation:

```
[root@compy ~]# gtf 1440 900 60
```

yielding:

```
# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync
```

The first line is a comment and need not be transferred. Paste or transcribe the Modeline anywhere inside the "Monitor" section that is referred to by the "Screen" section. Then make sure the "Screen" section includes the mode defined by your Modeline statement:

```
Section "Monitor"
    Identifier    "h193wk"
    Modeline      "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync
EndSection

(...)

Section "Screen"
    Identifier    "Screen1"
    Device        "nvidia0"
    Monitor       "h193wk"
    Subsection "Display"
        Depth     24
        Modes     "1440x900_60.00"
        ViewPort  0 0
    EndSubsection
EndSection
```

Running startX should yield an X session matching your monitor's resolution.

Before inserting the Modeline statement into your xorg.conf file, create a copy of xorg.conf so you can revert to the machine generated file if necessary.

If you have a problem after starting X, you may kill the X session by pressing <ctrl-alt-Backspace>.

Created by: freeminder last modification: Friday, March 31, 2006 [12:42:52 UTC] by hilmera 

---

### Post by Spoone on 2007-01-06
I tried this fix for my Norcent LM-965WA, to no avail.  I still can't get 1440x900.
Here's the output of my gtf command..:

 gtf 1440 900 60 

  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

Can anyone help?

Spoone

---

### Post by crimsonmx on 2007-03-10
You probably have either fixed this or given up by now, but you might also have to add a vertrefresh or horizsync line to your xorg.conf. I had to add in a vertrefresh line. Good luck

---

### Post by rickmans on 2007-03-11
I did all of the above (I think :P). And my xorg.conf is looking like mentioned below. The resolution is not selectable in the screenresolution window in gnome. Anyone tips how I can enjoy a 1440*900 resolution?

xorg.conf:
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

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/wacom"    # Change to 
                            # /dev/input/event
                            # for USB
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/wacom"    # Change to 
                            # /dev/input/event
                            # for USB
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/wacom"    # Change to 
                            # /dev/input/event
                            # for USB
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "PLE1900WS"
    VertRefresh     75.0 - 75.0
    Option        "DPMS"
    Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Monitor        "PLE1900WS"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1440x900_60.00" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1440x900_60.00" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1440x900_60.00" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1440x900_60.00" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1440x900_60.00" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1440x900_60.00" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

---

### Post by shekhark on 2007-03-14
Here is the updated link

[http://wiki.caoslinux.org/X_Server_Configuration](http://wiki.caoslinux.org/X_Server_Configuration)

This worked for me, but I am still having problems with colour depth. :(

---

