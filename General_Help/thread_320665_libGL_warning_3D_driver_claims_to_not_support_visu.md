---
title: "libGL warning: 3D driver claims to not support visual 0x4b"
date: 2006-12-17
forum: General Help
---

### Post by BlahMan_of.Doom on 2006-12-17
I get the  libGL warning: 3D driver claims to not support visual 0x4b error whenever I start up beryl, and my computer freezes. I have an X850Pro AGP (using aiglx) and I am running Ubuntu Edgy. Anyone know a way to prevent my computer from freezing?

---

### Post by silvagroup on 2006-12-18
I have the same problem. I am usisng a S3 ProSavage.
I also get the same error when trying to run WINE so it's not a beryl only problem. Looks more like hardware, must have something to do with the latest drivers included with ubuntu. I just installed 6.10 and did not have this problem with 5.10 at all. After a couple of days of messing with the install I tried Fedora Core 6 and had the same problem, so back to Ubunbtu 6.10. It could even be a kernel issue.
My quess is to look for some more drivers for you video. I am also trying to do that, not going well though. Seems silly that I would have to go back to 5.10 so that all my hardware works correctly, or run the gamit of trying different *.nix distros until I find one that works.
So hopefully some one has a good answer for us.
If yo come up with anything please post back, I will do so also.
Good luck.

---

### Post by joshd2189 on 2006-12-18
@BlahMan
I finally got beryl to work last night, but I still have "libGL warning: 3D driver claims to not support visual 0x5b" show up when I try to run 3D programs.  This prevents me from using the water plugin for beryl... I think.  When I was trying to install beryl, I also had my screen freeze up-many times.  I pinpointed the source of my problem in the /etc/X11/xorg.conf file.

run this in a terminal:
gksudo gedit /etc/X11/xorg.conf

look under the "Module" section and comment out the line with GLcore (this is what caused my computer to freeze like yours) .  Also check to make sure u have glx and dri loading

Section "Module"
        Load	"dbe"
	Load	"dri"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
#      Load	"GLcore"

Make sure the you have the following their respective sections:

Under "Device" section:
Option  	"XAANoOffscreenPixmaps"

Under "ServerLayout" section:
Option         "AIGLX" "true"

And the following sections:

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Oh and add beryl-manager in your startup programs:
System->Preferences->Sessions->Startup Programs->add->beryl-manager

finally restart your xsession by rebooting or #sudo /etc/init.d/gdm restart

I have a Mobile 915GM/PM/GMS/910GML graphics card and running edgy.  I have read that this libGL warning only happens in edgy and not in dapper. 
I hope that fixes your problem with beryl.  if not post your xorg.conf file and /etc/gdm/gdm.conf-custom contents and any other useful tidbits.  I am sorry I cant help anyone with the libGL warning, because I cant figure it out myself!

Also sorry about the messy post, this is my first post ever.  I figured I would join the community instead of just leeching off of it ;)  I hope some of this helped.  Now if somebody can come along and help all of us out with that libGL warning, that would be great.

---

### Post by silvagroup on 2006-12-19
joshd2189, thanks :)  looked at all that and it's all OK.
I can run ```
glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x42
2290 frames in 5.0 seconds = 457.963 FPS
 
``` but I can't run wine or beryl.[-( 
From what I can tell :-k  all the right stuff is in the xorg.conf (little that I know) so it should work.:twisted: 
I am stuck](*,)

---

### Post by BlahMan_of.Doom on 2006-12-31
> **joshd2189 said:**
> @BlahMan
I finally got beryl to work last night, but I still have "libGL warning: 3D driver claims to not support visual 0x5b" show up when I try to run 3D programs.  This prevents me from using the water plugin for beryl... I think.  When I was trying to install beryl, I also had my screen freeze up-many times.  I pinpointed the source of my problem in the /etc/X11/xorg.conf file.

run this in a terminal:
gksudo gedit /etc/X11/xorg.conf

look under the "Module" section and comment out the line with GLcore (this is what caused my computer to freeze like yours) .  Also check to make sure u have glx and dri loading

Section "Module"
        Load	"dbe"
	Load	"dri"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
#      Load	"GLcore"

Make sure the you have the following their respective sections:

Under "Device" section:
Option  	"XAANoOffscreenPixmaps"

Under "ServerLayout" section:
Option         "AIGLX" "true"

And the following sections:

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Oh and add beryl-manager in your startup programs:
System->Preferences->Sessions->Startup Programs->add->beryl-manager

finally restart your xsession by rebooting or #sudo /etc/init.d/gdm restart

I have a Mobile 915GM/PM/GMS/910GML graphics card and running edgy.  I have read that this libGL warning only happens in edgy and not in dapper. 
I hope that fixes your problem with beryl.  if not post your xorg.conf file and /etc/gdm/gdm.conf-custom contents and any other useful tidbits.  I am sorry I cant help anyone with the libGL warning, because I cant figure it out myself!

Also sorry about the messy post, this is my first post ever.  I figured I would join the community instead of just leeching off of it ;)  I hope some of this helped.  Now if somebody can come along and help all of us out with that libGL warning, that would be great.

My xorg has all that. Nothing works. Here's my xorg :\

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
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option	    "AIGLX" "true"
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
	Load  "dbe"
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
	Identifier   "L90D Analog"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X850 Pro (R481)"
	Driver      "ati"
	Option	    "XAANoOffscreenPixmaps"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X850 Pro (R481)"
	Monitor    "L90D Analog"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "false"
EndSection

```

---

### Post by DarkN00b on 2006-12-31
```
 libGL warning: 3D driver claims to not support visual 0x4b
```

This means your video card cannot display truecolor in 32 or more planes. This is a hardware limitation and afaik cannot be overcome by changing your settings.

Here is a list of visualIDs:
```
                0x23 : TrueColor       /  24 planes
                0x24 : TrueColor       /  24 planes
                0x25 : TrueColor       /  24 planes
                0x26 : TrueColor       /  24 planes
                0x27 : TrueColor       /  24 planes
                0x28 : TrueColor       /  24 planes
                0x29 : TrueColor       /  24 planes
                0x2a : TrueColor       /  24 planes
                0x2b : DirectColor     /  24 planes
                0x2c : DirectColor     /  24 planes
                0x2d : DirectColor     /  24 planes
                0x2e : DirectColor     /  24 planes
                0x2f : DirectColor     /  24 planes
                0x30 : DirectColor     /  24 planes
                0x31 : DirectColor     /  24 planes
                0x32 : DirectColor     /  24 planes
                0x4b : TrueColor       /  32 planes
```

This is not a comprehensive list, but it should give you some idea what I'm talking about. I get this same thing on my Intel 82852/82855 integrated video. AIGLX and Beryl work fine on my laptop though. I just can't use the rain plugin. :(

---

### Post by kaveraj on 2007-01-12
Thanks a million josh. After hours and hours of tweaking, I finally got beryl working on my dell laptop with your instructions...

Thanks for sharing the info.

---

