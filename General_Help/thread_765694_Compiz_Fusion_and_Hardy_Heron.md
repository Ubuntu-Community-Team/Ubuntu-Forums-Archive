---
title: "Compiz Fusion and Hardy Heron"
date: 2008-04-24
forum: General Help
---

### Post by nystud162 on 2008-04-24
So I just updated to Hardy Heron a few hours ago and when I booted up into it, Compiz Fusion wasn't working. I'm running with a Nvidia GeForce FX 5200.

Heres my output for "compiz --replace":
```
evan@evan-desktop:~$ compiz --replaceChecking for Xgl: not present. 
Detected PCI ID for VGA: 03:01.0 0300: 1002:5159 (prog-if 00 [VGA controller])
03:02.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
Segmentation fault
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"



```

Here is my output for "lspci":
```
evan@evan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 Display controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Multimedia controller: ATI Technologies Inc Unknown device 4d53
03:01.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
03:02.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)

```

And here is my output for "glxinfo | grep direct":
```
evan@evan-desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

---

### Post by grannyw on 2008-04-24
run 

```
compiz
```

try if it began to work
  else
      show me what u get in terminal

---

### Post by grannyw on 2008-04-24
```
$sudo apt-get xserver-xgl
```

u dont have xgl installed

---

### Post by grannyw on 2008-04-24
and what video card do u have???FX5200??

---

### Post by nystud162 on 2008-04-24
I have a Nvidia FX 5200.

Output of "compiz":
```
evan@evan-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:01.0 0300: 1002:5159 (prog-if 00 [VGA controller])
03:02.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
Segmentation fault
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

output:
```
evan@evan-desktop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

```

---

### Post by grannyw on 2008-04-24
i think that u should try to install xserver-xgl from synaptic package manager,i think that it will fix it,but if something gets wrong u can just run
```
$sudo apt-get remove xserver-xgl
```

try it

---

### Post by Jesus_Valdez on 2008-04-24
I have the same problem and install xserver-xgl did'nt work. 

My output of "compiz"

> ~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Advertencia del gestor de ventanas: 0 almacenado en la clave GConf /apps/metacity/general/num_workspaces no es un número razonable de áreas de trabajo. El máximo disponible es de 36
valdez@valdez-laptop:~$ 


---

### Post by fabiomb on 2008-04-25
can you post your /etc/X11/xorg.conf?

---

### Post by Jesus_Valdez on 2008-04-25
here's my /etc/X11/xorg.conf

I just uninstall xserver-xgl because the windows began to update strangely, like in segments, i cant explain but the point is some how  mess up whit the graphics

> #


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"mx"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by fabiomb on 2008-04-25
eh! you said you have an nVidia FX5200 but this conf says: "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"

WTF?

---

### Post by Jesus_Valdez on 2008-04-25
we are two diferent guys.

---

### Post by nystud162 on 2008-04-26
> **fabiomb said:**
> can you post your /etc/X11/xorg.conf?

Im the thread starter, the other guy is presenting his problem thats simular to mine in the same thread, as requested, here is my "/etc/X11/xorg.conf":

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"v4l"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce"
	Busid		"PCI:3:2:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E173FP"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
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
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"Intel 915"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "device" #   
	Identifier	"device2"
	Boardname	"ATI Radeon"
	Busid		"PCI:3:1:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #   
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" #   
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "device" #   
	Identifier	"device3"
	Boardname	"NVIDIA GeForce"
	Busid		"PCI:3:2:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #   
	Identifier	"screen3"
	Device		"device3"
	Defaultdepth	24
	Monitor		"monitor3"
EndSection
Section "monitor" #   
	Identifier	"monitor3"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Zorael on 2008-04-26
The fix-it-all answer for upgraders would be to make sure you've disabled third-party repositories, **completely remove** compiz packages, and then reinstall them.
```
$ sudo apt-get autoremove --purge compiz* libcompiz* libdeco* emerald* libemerald*
```

This will, hopefully, take care of segmentation faults. As for nystud's xorg file, it looks needlessly complicated. I suggest you make a backup of it, and then generate a fresh one.
```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by nystud162 on 2008-04-26
> **Zorael said:**
> The fix-it-all answer for upgraders would be to make sure you've disabled third-party repositories, **completely remove** compiz packages, and then reinstall them.
```
$ sudo apt-get autoremove --purge compiz* libcompiz* libdeco* emerald* libemerald*
```

This will, hopefully, take care of segmentation faults. As for nystud's xorg file, it looks needlessly complicated. I suggest you make a backup of it, and then generate a fresh one.
```
$ sudo dpkg-reconfigure xserver-xorg
```

After I executed: ```
$ sudo dpkg-reconfigure xserver-xorg
```
And went through the reconfiguration (oddly It only brought me to edit keyboard settings). I then restarted my computer and when I run "compiz" I get:
```
evan@evan-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

Also, I keep enabling the "Nvidia Accelerated Graphics Driver" in System -> Administration -> Hardware Drivers and after I do the required restart, It's always still disabled.

---

### Post by Zorael on 2008-04-26
> **nystud162 said:**
> Also, I keep enabling the "Nvidia Accelerated Graphics Driver" in System -> Administration -> Hardware Drivers and after I do the required restart, It's always still disabled.
You could try to manually install and enable the driver.
```
$ sudo aptitude install nvidia-glx-new
```
Then edit your xorg.conf, find the Device section that represents your video card (could say Generic Video Card, could say Configured Video Card), and change the Driver entry to "nvidia". If there is no driver entry, create one. :>
```
Driver "nvidia"
```

---

### Post by nystud162 on 2008-04-26
Okay, so It works, THANKS!
Only thing right now is that my icons didn't show up on my desktop...
Maybe it's just a one time glitch and I'll restart and see if it does it again.

THANKS AGAIN.

---

### Post by nystud162 on 2008-04-26
All is good, desktop icons and all.
Thanks You

---

### Post by mcmunt on 2008-04-27
Will try the removal option for my problems too, as they're much the same.

Thanks for the info.

---

### Post by Zorael on 2008-04-27
What happens is that your old, Gutsy version of compiz was likely grabbed from outside the official repositories. As such, now in your Hardy installation it tries to update it with the new "official" version, **assuming** it's an old "official" version, and stuff goes wrong. Version mismatches, breakage.

So the general fix is to make sure you've disabled extra repositories which might contain compiz in your software sources, then completely removing compiz (or whatever app won't work, could be awn, could be whatever you got from git/compiled yourself, as long as it's an "external" and unsupported build), then reinstalling. You may get some errors here and there unless you reset your Compiz profile in the settings manager (ccsm), but you'll notice. Also, if you're to redo them, setting the Backend to flat-file is always a good idea.

Having xserver-xgl installed makes Compiz render everything in software mode, so major slowdowns.

---

