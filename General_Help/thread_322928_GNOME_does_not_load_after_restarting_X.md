---
title: "GNOME does not load after restarting X"
date: 2006-12-21
forum: General Help
---

### Post by lightrush on 2006-12-21
Shortly, I checked forums out and saw that many people are experiencing same symptoms, but the causes are different so one thing helps three but doesn't the other 2. I did not see any working solution to this issue and I saw other people having it...

OK. Here is what is happening here:

(1) When I start up the machine from Power off or Restart - everything runs fine - boot process, X is starting, logging in, Gnome starts - just fine.

(2) If I log out and log in again from working session - everything is fine also.

(3) If I restart the X by hitting Ctrl+Alt+Backspc - X starts, login screen appears, logs in, I hear the login sound BUT HERE nothing more happens. I do not see the splash image, nothing is loading (no hard disk activity) and all I see is mouse cursor on plain black/brown (I changed the black to black). And whatever times I restart the X with the 3-keys I get the same thing. None of the other sessions work except for the Failsafe Terminal. The only thing that fixes the thing is rebooting the  PC either from the login window or by hitting F13. Then everything goes fine like described in (1) and (2).](*,) ](*,) 

Running i386 Edgy on AMD64 + NF4U + GF7. NVIDIA drivers for video are installed and running fine (games are being played w/o problem).:( 

In log files the error appears as: gdm[4165]: Error reinitilizing server

Any ideas on the matter? Any questions - I will answer everything, please help me on this one.


PS:

The intersting thing here is that - there should be a problem for this to happen. And how come it overcomes it when booting and not when restarting X ... :confused: I think that the probability of bug is less than the probability of problem here. I dont know since when is this happening because I do not Ctrl+Alt+Backspace all day long. I noticed it these days and the thing is that I dont want to get my desktop disabled... :)

---

### Post by lightrush on 2006-12-22
Isn't there anyone having an experience on this matter?

---

### Post by sup on 2006-12-27
well I have exactly the same problem. only that it does not work for me when I log off as well as when I hit ALT+CTRL+backspace.

I recently tried xgl+compiz (I am running proprietary drivers for ati (form ubuntu repositories), Edgy Eft, i386) - actually yesterday, and then it seemed to work. So I removed all the three packages that got installed but it still does not work:-/.
I do not mind it that much since I do not need to log off at all, but it is a kind of nuisance.

btw - is there any history for apt-get?

---

### Post by sup on 2006-12-27
well, I just tried loging off and it even does not get me to login screen. I use autologin so I do not know what happens at first login screen, but I expect it works fine. I do not really want to try it, however - what if it broke X completely:-D.

---

### Post by LenzM on 2006-12-27
Try going to the failsafe terminal and starting x by running
```
 startx 
```

If that doesn't work it should at least give an error output.

---

### Post by sup on 2006-12-27
```
xauth:  creating new authority file /home/tom/.serverauth.5080


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux bill 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 28 01:30:00 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwertz)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+cz(qwerty)+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
ProcXCloseDevice to close or not ?
Synaptics DeviceOff called
xinit:  connection to X server lost.
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


```
is the output. AFAIK ATI cards with proprietary drives od not support AIGLX, maybe there is a problem?

this is my xorg.conf 
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
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#	Identifier  "stylus"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#	Identifier  "cursor"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "cursor"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "ServerLayout"

#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
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
	Load  "synaptics"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "cz"
	Option	    "XkbOptions" "lv3:ralt_switch"
	Option	    "XkbVariant" "qwerty"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "100"
#	
	Option	    "LeftEdge" "1700"
	Option	    "RightEdge" "5300"
	Option	    "TopEdge" "1700"
	Option	    "BottomEdge" "4200"
	Option	    "FingerLow" "25"
	Option	    "FingerHigh" "30"
	Option	    "MaxTapTime" "180"
	Option	    "MaxTapMove" "220"
	Option	    "VertScrollDelta" "100"
	Option	    "MinSpeed" "0.09"
	Option	    "MaxSpeed" "0.18"
	Option	    "AccelFactor" "0.015"
	Option	    "SHMConfig" "on"
#always usefull
	Option	    "Emulate3Buttons" "on"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
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
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth      24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection


```

---

### Post by sup on 2006-12-29
so I tried to go back to my very first backup of xorg.conf, which did not help, then I tried mesa drivers (ati in xorg.conf) and it gave longer output  (i do not knowif more useful) but it still does not work - so it is not directly related to xorg.conf or to proprietary drivers.
the log is as follows
```
xauth:  creating new authority file /home/tom/.serverauth.4992
xauth:  creating new authority file /home/tom/.Xauthority
xauth:  creating new authority file /home/tom/.Xauthority

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux bill 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 29 19:25:37 2006
(==) Using config file: "/etc/X11/xorg.conf"
(**) RADEON(0): RADEONPreInit
(**) RADEON(0): RADEONScreenInit d8000000 0
(**) RADEON(0): Map: 0xd8000000, 0x04000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81fd108)
(**) RADEON(0): Read: 0x00180006 0x00040048 0x00000000
(**) RADEON(0): Read: rd=6, fd=72, pd=4
(**) RADEON(0): RADEONSaveMode returns 0x81fd108
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x04000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1400x1050     108.00  1400 34208 34320 1688  1050 1052 1055 1063 (24,32)
1400x1050     108.00  1400 34208 34320 1688  1050 1052 1055 1063 (24,32)
(**) RADEON(0): Pitch = 11534512 bytes (virtualX = 1400, displayWidth = 1408)
(**) RADEON(0): RADEONInit returns 0x81fdab8
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fdab8)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00000006 0x00010030 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=6, fd=48, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20237c7c
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(**) RADEON(0): Initializing backing store
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 176
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(**) RADEON(0): RADEONScreenInit finished
(EE) AIGLX: DRI module not loaded
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwertz)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+cz(qwerty)+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc104)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
ProcXCloseDevice to close or not ?
Synaptics DeviceOff called
xinit:  connection to X server lost.
(**) RADEON(0): RADEONCloseScreen
(**) RADEON(0): RADEONDRIStop
(**) RADEON(0): RADEONDisplayPowerManagementSet(0,0x0)

waiting for X server to shut down (**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fd108)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00180006 0x00040048 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=6, fd=72, pd=4
(**) RADEON(0): Disposing accel...
(**) RADEON(0): Disposing cusor info
(**) RADEON(0): Disposing DGA
(**) RADEON(0): Unmapping memory
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

---

### Post by riven0 on 2006-12-29
How about reinstalling gdm and the xserver? Did you guys try that?:
> 
sudo apt-get install --reinstall gdm && sudo apt-get install --reinstall xserver-xorg

---

### Post by sup on 2006-12-29
yep, I tried that now. I also tried xdm instead of gdm, without success. However, I tried to install fluxbox, and when I chose that as a session, it logs in fine. So there is something wrong with GNOME, it seems. No idea what, really.

I would like to open a bug for it if I knew 1) it is a bug 2) how to describe it:-). but it is probabyl something messed up with my installation. However, I have no idea what, i have not been playing with it that much

---

### Post by lightrush on 2006-12-29
Ahh no success here either .. 

I dont know.. I start thinking that it IS a bug.. because at install point there was no such problem. This came sometime later on and I have a feeling that it came after some update. But still - this is only intuition :).

---

### Post by sup on 2006-12-30
So i created a [bug report]("https://bugs.launchpad.net/distros/ubuntu/+bug/77505")

---

### Post by ravenon on 2006-12-30
Is everybody in this thread running i386 Edgy on a 64 bit machine? I tried that two months ago and had the same problems described above: in fact often on choosing shutdown, my screen would go blank and machine would freeze, similarly for logout out and login. I never did find a solution except to install the 64 bit version. For what ever reason, all works now.

---

### Post by sup on 2006-12-30
I am on I386 here...

---

### Post by sup on 2007-01-29
So the problem seems to have disappeared since I can now logout and login to gnome without problems. It might have something to do with recent updates to some gnome-files...

---

### Post by strabes on 2007-01-29
i386 here and I had the same problem. running ati X1400 with fglrx.

---

