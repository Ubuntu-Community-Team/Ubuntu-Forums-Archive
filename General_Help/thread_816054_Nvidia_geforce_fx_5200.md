---
title: "Nvidia geforce fx 5200"
date: 2008-06-02
forum: General Help
---

### Post by miickEe on 2008-06-02
Hey

Running Need For Speed Most Wanted on ubuntu 7.10 with cedega runs very slow. I'm sure this graphics card is more than capable of running this old game. However, I may be mistaken. Or maybe I need an updated driver.

Any suggestions?

EDIT:
What settings did you have on your cedega or likewise to produce optimal results?

Prompt and complete help will be greatly appreciated.

Thanks in advance

miickee

---

### Post by ChameleonDave on 2008-06-02
I (or rather my girlfriend) have an NVidia FX5200.  3D games work just fine on it, though they are not as zippy as on my NVidia 7900 GS.  For example, Civilization IV (on Windows) is rather choppy on the FX5200.  It is essentially the oldest 3D card that you can get away with these days.

Either you have 3D acceleration enabled or you don't.  To find out, run a program that requires it.  These include compiz, amoeba, neverball, alien-arena and foobilliard.  If any of those work, then you are properly configured.  Otherwise, you will need to install and enable the proper driver.

---

### Post by pedro_orange on 2008-06-02
```
glxinfo | grep rendering
```

Will tell you if you have the ability to 3D render.

Have you tried running the game in WINE rather than Cedega? 

You have to remember, these games are written for Windows. Not for Linux. Don't expect them to work. Just be over the moon when they do, and don't complain when they don't :)

---

### Post by miickEe on 2008-06-02
> I (or rather my girlfriend) have an NVidia FX5200. 3D games work just fine on it, though they are not as zippy as on my NVidia 7900 GS. For example, Civilization IV (on Windows) is rather choppy on the FX5200. It is essentially the oldest 3D card that you can get away with these days.

Either you have 3D acceleration enabled or you don't. To find out, run a program that requires it. These include compiz, amoeba, neverball, alien-arena and foobilliard. If any of those work, then you are properly configured. Otherwise, you will need to install and enable the proper driver.
Yeah, I'm running compiz and it's awesome.

```
miickee@miickee-gutsy:~$ glxinfo | grep rendering
direct rendering: Yes

```

I understand that but I hear a lot of people are having success with it and I want in. Maybe I should buy a new gfx card. Just wondering whether or not it was absolutely necessary before I actually did lol.

---

### Post by pedro_orange on 2008-06-02
Ok. Well I don't have the game - So I can't test this for you.

The best I can offer you is this advise:

Read and try what the guys on the WINEHQ AppDB suggest: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2577](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2577)

If that doesn't work, make a post in the WINE Ubuntuforums. You may find more joy there.

Good luck.

---

### Post by miickEe on 2008-06-02
I eventually got nfsmw to install using wine 0.9.54, but I had to copy the files from the cdrom to a folder, and modify the autorun.cfg file to directx value of 0, and some other value to 0. It managed to install, cause every other time it would just kill over and say it needed direct x, even after trying to install it separately.

Anyone else had success installing need for speed most wanted in wine?

---

### Post by fragos on 2008-06-02
The nvidia-glx-new package supports the FX5200. It's Nvidia version number is 169.12. My FX5200 reports 1100 fps with glxgears which is the same I get with m Dell 1420n laptop which has the Intel X3100 GPU. I'm not a gamer so I may not be demanding as much as you are from my GPU.

---

### Post by jabeez on 2008-06-02
I don't really game in Linux, so sorry if this seems too obvious, but do you disable compiz when you game?

---

### Post by RAOF on 2008-06-02
> **fragos said:**
> ...My FX5200 reports 1100 fps with glxgears which is the same I get with m Dell 1420n laptop which has the Intel X3100 GPU...

Which only goes to show how utterly meaningless the FPS numbers from glxgears are :).

---

### Post by miickEe on 2008-06-02
> I don't really game in Linux, so sorry if this seems too obvious, but do you disable compiz when you game?

You know what, it does make a noticeable difference when I turn off compiz. However, it's still not playable even with compiz turned off.


> The nvidia-glx-new package supports the FX5200. It's Nvidia version number is 169.12. My FX5200 reports 1100 fps with glxgears which is the same I get with m Dell 1420n laptop which has the Intel X3100 GPU. I'm not a gamer so I may not be demanding as much as you are from my GPU.

How do I check the version number of my drivers? And if mine are old, how do I update them? Any other ways to optimise gfx performance?

Also what else should I check/uncheck in cedega/wine to experience better gfx performance?

**EDIT: IMPORTANT**
```
miickee@miickee-gutsy:~$ cat /proc/driver/nvidia/agp/status && cat /proc/cpuinfo | grep MHz
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled
cpu MHz         : 2202.992
miickee@miickee-gutsy:~$ glxgears
2310 frames in 5.0 seconds = 461.823 FPS
958 frames in 6.3 seconds = 151.071 FPS
```

---

### Post by fragos on 2008-06-03
Although true that glxgears isn't a scientifc measurement it does provide better comparative data points than visual inspection and it's available in perhaps all Linux distros. It's probably best not to adjust the the default window size since that will change the the reported results as will running other display intensive tasks at the same time. Keeping as many variables as posible fixed will yield consistent results. Maximizing the the glxgeras window to 1440x900 dropped my measured results to 46 fps.

---

### Post by fragos on 2008-06-03
"nvidia-settings" will provide the version and a lot of other interesting things.

---

### Post by RAOF on 2008-06-03
> **fragos said:**
> Although true that glxgears isn't a scientifc measurement it does provide better comparative data points than visual inspection and it's available in perhaps all Linux distros. It's probably best not to adjust the the default window size since that will change the the reported results as will running other display intensive tasks at the same time. Keeping as many variables as posible fixed will yield consistent results. Maximizing the the glxgeras window to 1440x900 dropped my measured results to 46 fps.

It's true that glxgears will give consistent results.  They just won't really correspond to interesting 3d performance :).  The bottleneck for glxgears is pushing pixels to the screen, which is not the bottleneck for any 3d that you care about.  Higher glxgears FPS will often correlate to better 3d performance, but only by accident!

---

### Post by miickEe on 2008-06-03
nvidia-settings yielded:
```

Operating System: Linux-x86
NVIDIA Driver Version: 100.14.19

```

And I've edited the xorg.conf file accordingly:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"RenderAccel"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"CMC 22 W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"CMC 22 W"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1680"	"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by RAOF on 2008-06-03
Your card should be supported by the nvidia-glx-new (169.17, or something) drivers.  It should be as easy as 'sudo aptitude install nvidia-glx-new' in a terminal to install them.

---

### Post by miickEe on 2008-06-03
```


miickee@miickee-gutsy:~$ sudo aptitude install nvidia-glx-new
[sudo] password for miickee:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been kept back:
  wine 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   
```

---

### Post by fragos on 2008-06-03
Ubuntu 8.04 would have installed 169.12 and xorg.conf would have been set up for you. my xorg.conf is much simpler. The only changes I made were for my Wacom Graphire4 -- it follows:

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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Stylus2" 	"3"  # set button to right click
	Option		"Type"		"stylus"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"        "/dev/input/wacom"
	Option		"Type"          "pad"
	Option		"USB"           "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
EndSection

Section "Module"
	Load		"glx"
EndSection

---

### Post by miickEe on 2008-06-03
I had just recently downgraded from hardy to gutsy, I'm finding gutsy is a lot happier with my hardware than with hardy.

---

### Post by miickEe on 2008-06-04
I find that most others who have this card can even play half life 2 (minimal settings), which is disturbing. So what if I buy a much better card, say, a 8600GT 256MB ddr3 card? What if I don't achieve the best out of that card like I am at the moment? Wouldn't that be a waste of money?

So that's why I want to know how to get the best out of this card so I know when I buy a new one that it's not a wasted purchase.

I went into System -> Administration -> Restricted Hardware Drivers and clicked on the driver for nvidia, and it apparently installed "nvidia-glx-new". But when I type:

```

nvidia-settings

```
It shows me the same driver version. :S

---

### Post by fragos on 2008-06-04
Running a recent driver is IMHO a good idea but I doubt you will see an improvement in performance with an older card like the FX5200.

---

### Post by miickEe on 2008-06-04
I'm thinking of getting a Gigabyte, XFX or Asus geforce 8600GT 256mb GDDR3 video card. Do you think that would be compatible with linux?

I've checked the linux hardware compatibility wiki and it says:
> 
GeForce 8600GT 512MB 128-bit GDDR3 PCI Express x16 HDCP Ready SLI Supported

Wondering if that also extends to the 256mb version, or the overclocked 730MHz GTS.

---

### Post by ChameleonDave on 2008-06-04
> **miickEe said:**
> I find that most others who have this card can even play half life 2 (minimal settings), which is disturbing. So what if I buy a much better card, say, a 8600GT 256MB ddr3 card?

Upgrading from an ancient FX5200 will improve performance more than a year of tweaking.

I have a 7900 GS, and I am satisfied with it on Ubuntu and XP.  The FX5200 just doesn't make the grade any more.

---

