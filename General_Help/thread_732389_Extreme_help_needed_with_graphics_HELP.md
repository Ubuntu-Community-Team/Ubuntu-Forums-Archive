---
title: "Extreme help needed with graphics HELP"
date: 2008-03-22
forum: General Help
---

### Post by willy111123 on 2008-03-22
I currently have a laptop using a 9600 ATI radeon card. I have been playing around a lot trying to get COMPIZ and BERLY to work properly. Somehow I have really crippled the system. I have made backups of the xorg.conf file and have restored them, but it is not fixing the problem. When I log into Ubuntu 7.10 I now receive a little black X and login is slow. When I try to open a terminal window I see an outline of a box appear and move out until the screen is full and then the terminal window opens. The graphics are extremelly slow. Can someone please help me . I do not want to reinstall. I must have removed some core process. FXGL or Xserver, I dont know. Someone please help me.

---

### Post by Nameless_one on 2008-03-22
I believe that if you open your xorg.conf file, in the Device section for the graphics driver, you will see 'vesa' as the driver. If that is the case, then what you are experiencing is normal, vesa is a very slow graphics driver suited for old cards. Either install the fglrx driver from the repositories, or the radeon open-source driver and you'll be fine.

---

### Post by willy111123 on 2008-03-22
No actually the Xorg.conf file has ATI as the driver and the Identifier as the full identity of the ATI driver

---

### Post by Nameless_one on 2008-03-22
That's odd. I'm sorry I don't know what else might have happened. Maybe you should trace back your steps and check everything.

---

### Post by willy111123 on 2008-03-22
Here is my xorg.conf file

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
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"AllowGLXWithComposite" "true"
	Option 		"GARTSize" "64"
	Option 		"MergedFB" "off"
	Option 		"XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes		"1680x1050" "1440x900"
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

### Post by willy111123 on 2008-03-22
This is my history I did when this happened

  251  nano /etc/X11/xorg.conf
  252  glxinfo | grep direct
  253  grep -i aiglx /var/log/Xorg.0.log
  254  gedit /etc/X11/xorg.conf
  255  grep -i aiglx /var/log/Xorg.0.log
  256  grep -e EE -e WW /var/log/Xorg.0.log
  257  gedit /etc/X11/xorg.conf
  258  cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup2
  259  apt-get fglrx-new
  260  apt-get install fglrx-new
  261  apt-get update\
  262  apt-get update
  263  nano /etc/X11/xorg.conf
  264  gedit /etc/X11/xorg.conf
  265  gedit ~/.config/compiz/compiz-manager
  266  glxinfo | grep vendor
  267  sudo modprobe -r fglrx
  268  glxinfo | grep vendor
  269  apt-get install xserver-xorg-video-ati
  270  nano /etc/X11/xorg.conf
  271  history
  272  264 history
  273  264 history 264
  274  gedit /etc/X11/xorg.conf
  275  gedit /etc/X11/xorg.conf
  276  sudo apt-get install xserver-xgl
  277  cp /etc/X11/xorg.conf.backup2 /etc/X11/xorg.conf

---

