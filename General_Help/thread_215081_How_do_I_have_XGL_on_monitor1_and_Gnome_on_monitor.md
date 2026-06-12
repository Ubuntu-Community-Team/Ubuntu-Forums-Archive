---
title: "How do I have XGL on monitor1 and Gnome on monitor2?"
date: 2006-07-13
forum: General Help
---

### Post by Mr_J_ on 2006-07-13
I have two monitors and I'd like to have XGL running on both monitors, but since that far off in my perception, I'd like the next best thing.

I'd like to have XGL running on my Dell Ultrasharp 1907FP threw DVI @ 1280x1024 24bit.
On my Sony trinitron multiscan 200es crt I'd like Gnome, since I believe I can't have XGL there. The CRT is working threw VGA @ 1024x768 24bit.

Is this possible or just not realistic?

I have a:
AMD 2GHZ Venice
512MB DDR400
Nvidia 6600GT
-

Is it possible, or just not recomended?

I'm going to do a fresh install of dapper drake soon, and I'd like to have it up and running soon after that.

How would I go about this?

---

### Post by Maggot on 2006-07-13
I don't believe its possible ....

You could run 2 different X Servers with 2 different config files but that just seems crazy :)

---

### Post by Mr_J_ on 2006-07-13
So it might just be smarter to not use 1 of the monitors?

---

### Post by Maggot on 2006-07-13
Depends on your needs.  Xgl was cool for a bit but I didn't find it very useful.  To me its more eye candy than anything else.

I'd go with normal X server with dual monitors

---

### Post by Dommel on 2006-07-13
> **Mr_J_ said:**
> I have two monitors and I'd like to have XGL running on both monitors, but since that far off in my perception, I'd like the next best thing.



Why cant you have XGL running on both monitors? I have a 6600GT and I run XGL in dual sceen setup without any problems. You lose Xinerama/Twinview functionality but it's still workable. And the monitors are different resolutions as well, 1600x1200 and the other one 1280x1024.

[img]http://www.mmorpg.nl/images/XGL/Screenshot2_resize.jpg[/img]

[img]http://www.mmorpg.nl/images/XGL/Screenshot3_resize.jpg[/img]

---

### Post by Mr_J_ on 2006-07-14
Could you explain how you did that?
Where you learned how to do that?

Most of the people I've spoken to always say that XGL can't go to dual monitors...

I have a 660GT myself so that is interesting because that is exactly what I wanted.

---

### Post by jstroot on 2006-07-14
I have used twinview in the past, and apted against setting up two xservers. I haven't tried, but two seperate xservers may not be a bad way to go for getting xgl on both. 
Just remember, with two xservers, you cannot drag windows from one screen to the other.

--jstroot

---

### Post by jstroot on 2006-07-14
> **Dommel said:**
> Why cant you have XGL running on both monitors? I have a 6600GT and I run XGL in dual sceen setup without any problems. You lose Xinerama/Twinview functionality but it's still workable. And the monitors are different resolutions as well, 1600x1200 and the other one 1280x1024.



Why do you have tweo seperate resolutions? Are you using different monitors, or is there some issue you ran into with the setup?

--jstroot

---

### Post by jstroot on 2006-07-14
Here is a dual monitor how-to for nvidia cards. It is on the gentoo wiki, but since it is for nvidia cards, it should still work.

[NOTE: I have not tried this myself. This shoulld work, "theoretically".]

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_a_dual.2Ftri.2Fmulti-head_graphics_card](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_a_dual.2Ftri.2Fmulti-head_graphics_card)

and more specifically

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Non-TwinView](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Non-TwinView)

That should at least set you in the right direction in getting xgl on two monitors.

--jstroot

---

### Post by Mr_J_ on 2006-07-14
I'm using two diferent and separate resolutions and two diferent frequencies because my my two monitors are just too diferent to have them match even one resolution.

---

### Post by Dommel on 2006-07-14
> **jstroot said:**
> Why do you have tweo seperate resolutions? Are you using different monitors, or is there some issue you ran into with the setup?

--jstroot

Main monitor is 20.1" and my 2nd monitor is 17", hence the different resolutions. I'll post my xorg.conf for the topic starter, other than that it's just installing XGL from the guides on this forum. Nothing extra needs to be done to get it working.

```

Section "Extensions"
#	Option	"Composite"	"Enable"
EndSection

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load "GLcore"
#	Load "bitmap"
#	Load "dri"
#	Load "int10"
#	Load "record"
#	Load "speedo"
 
    Load	"dbe"
    Load	"ddc"
    Load	"extmod"
    Load	"freetype"
    Load	"type1"
    Load	"glx"
    Load	"vbe"
EndSection

Section "ServerFlags"
#    Option	"DontZap"
#    Option	"DontZoom"

    Option	"blank time"	"100"

    Option	"standby time"	"100"
    Option	"suspend time"	"100"
    Option	"off time"	"100"

#    Option	"Xinerama"	"true"
EndSection

Section "InputDevice"
    Identifier	"Keyboard"
    Driver	"kbd"

    Option	"AutoRepeat"	"500 30"
    
    Option	"XkbModel"		"logiinkse"	# pc104euro logiink itouchin itouch
    Option	"XkbLayout"		"us" 
	Option	"XkbOptions"	"compose:rwin"
EndSection

Section "InputDevice"
    	Identifier	"Mouse"
    	Driver		"mouse"
	Option  "CorePointer"
	Option	"Protocol"	"ExplorerPS/2"
    	Option	"Device"	"/dev/input/mice"	
	Option	"ZAxisMapping"	"4 5"
	Option  "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
    Identifier	"TFT"

    HorizSync	30-80
    VertRefresh	50-60 #75
    Option	"dpms"

#   DisplaySize	650 260
EndSection

Section "Device"
    Identifier	"nVidia"

    Driver	"nvidia"

    Option	"NvAGP"			"1"
    Option	"NoLogo"		"true"
    Option	"RenderAccel"		"true"
    Option	"HWCursor"		"true"
    Option	"RandRRotation"		"true"

    Option	"IgnoreEDID"		"false"
    Option	"UseEdidFreqs"		"true"
    
    Option	"TwinView"
    Option	"TwinViewOrientation"		"LeftOf"
    Option	"SecondMonitorHorizSync"	"30-80"
    Option	"SecondMonitorVertRefresh"	"60"

    Option	"MetaModes"	"1280x1024, 1600x1200; NULL, 1280x1024; NULL, 1280x960; NULL, 1152x864; NULL, 1024x768; NULL, 800x600; NULL, 640x480"
   
EndSection

Section "Screen"
    Identifier	"Screen"
    Device	"nVidia"
    Monitor	"TFT"

    DefaultDepth 24

    SubSection "Display"
        Depth		24
        Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        ViewPort	0 0
    EndSubsection

    SubSection "Display"
        Depth		16
        Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        ViewPort	0 0
    EndSubsection

    SubSection "Display"
        Depth		8
        Modes		"640x480"
        ViewPort	0 0
        Virtual 	800 600
    EndSubsection

    SubSection "Display"
	Depth		4
        Modes		"640x480"
    EndSubSection

    SubSection "Display"
	Depth		1
        Modes		"640x480"
    EndSubSection

EndSection

Section "ServerLayout"
    Identifier	"Main Layout"

    Screen	"Screen"
    InputDevice	"Mouse"		"CorePointer"
    InputDevice "Keyboard"	"CoreKeyboard"
EndSection



```

---

### Post by Mr_J_ on 2006-07-15
I've used your xorg.conf as a basis for mine, and I've yet to see XGL running on both screens.

This is my /etc/X11/[COLOR="DarkOrange"]xorg.conf[/COLOR] :
> 
#Section "Extensions"
#	Option	"Composite"	"Enable"
#EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section	"ServerFlags"
#	Option	"DontZap"
#	Option	"DontZoom"

	Option	"blank time"	"100"

	Option	"standby time"	"100"
	Option	"suspend time"	"100"
	Option	"off time"	"100"

#	Option	"Xinerama"	"true"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#	Load	"GLcore"
#	Load	"bitmap"
#	Load	"dri"
#	Load	"int10"
#	Load	"record
#	Load	"speedo"

	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"type1"
	Load	"glx"
	Load	"vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "pt"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    	Identifier     "Multiscan200ES"

	HorizSync	30-70
	VertRefresh	50-120

    	Option		"DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"

	Option	"NoLogo"	"true"
	Option	"RenderAccel"	"true"
#	Option	"HWCursor"	"true"
#	Option	"RandRRotation"	"true"

#	Option	"IgnoreEDID"	"false"
#	Option	"UseEdidFreqs"	"true"

	Option	"TwinView"
	Option	"TwinViewOrientation"	"LeftOf"
	Option	"SecondMonitorHorizSync"	"30-81"
	Option	"SecondMonitorVertRefresh"	"60"

	Option	"MetaModes"	"1024x768, 1280x1024; NULL, 1280x1024;	NULL, 1024x768; NULL, 800x600; Null, 640x480"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Multiscan200ES"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
	ViewPort    0 0
    EndSubSection
EndSection



Also this is my /etc/gdm/[COLOR="DarkOrange"]gdm.conf-custom[/COLOR] :

> # GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

 [servers]

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true


I'm guessing your's diferent...
I think it's from this file that my XGL doesn't stretch to the second monitor. It does seem to be restricted to the one monitor.
It shows the larger resolution that I'd use if the second monitor was being used, and XGL does show the area for the second monitor, only all this is restricted to the first monitor. The second monitor even turns on, but a crossed background is all that is shown. My mouse can go there, but XGL doesn't use it at all. Xorg seems to recognize it tho.

---

### Post by Dommel on 2006-07-15
Did you try backupping your xorg.conf and just using mine (after editting resolutions ofcourse)?

I got my XGL running by following the first guide on the ubuntu wiki, nothing special was needed to get it running on dual monitors.

---

### Post by ricesteam on 2006-07-29
> I got my XGL running by following the first guide on the ubuntu wiki, nothing special was needed to get it running on dual monitors.

Can elaborate on this and help us noobs out? :D

---

### Post by Beamerboy on 2006-07-29
If you are using xgl/compiz from Quinn's repository dual monitors have been correctly supported for about 2 weeks now.  My setup is slightly different because I have 2x Dual Head cards (6600GTs) and I run one monitor on each card (will be upgrading to 4 monitors in the future).

Here is my xorg.conf

```

Section "ServerLayout"
  Identifier "Simple Layout"
  Screen      "Screen1"
  Screen      "Screen2" LeftOf "Screen1"
  Option      "Xinerama" "on"
  InputDevice    "Keyboard0" "CoreKeyboard"
  InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb.txt"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 155.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Screenshot is [HERE](http://www.paladine.org.uk/images/windows+linux.png)

And to make things a little easier for you, [here](http://www.ubuntuforums.org/showthread.php?t=222034) is a HOWTO I wrote recently for XGL+Compiz on 32bit Dapper for Nvidia Graphics Cards and a Gnome Environment.

BeamerBoy

---

### Post by ricesteam on 2006-07-29
How about with AIGLX and ATI cards?

---

