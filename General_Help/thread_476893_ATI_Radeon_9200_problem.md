---
title: "ATI Radeon 9200 problem"
date: 2007-06-17
forum: General Help
---

### Post by Page on 2007-06-17
I read a [tutorial](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way) on getting my ATI card (Radeon 9200SE) working in Ubuntu, but this process caused my xorg.conf  to be overwritten with a broken copy that produced a blank screen instead of a login prompt. (fortunately I had backed  up the good file)

I also tried to add the driver via the restricted drivers module in GNOME, but the module claimed that I needed no restricted drivers. 

Is there a better way to get my ATI driver working?

---

### Post by Page on 2007-06-17
anyone?

---

### Post by qamelian on 2007-06-17
> **Page said:**
> anyone?

You'll need to go to the ATI web site and download an old version of their driver from their archives. Unfortunately, your card is no longer supported by the newest drivers. You might also try Envy, found at [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) .This utility has helped many folks install ATI and Nvidia drivers and I believe it will download and install the latest driver that still supports your card.

---

### Post by Page on 2007-06-17
Envy produced the following output:

```

Envy Error: ATI's legacy driver does not support your operative system

```

Installing the ATI driver manually through envy created the same problem I described in the beginning of this thread. 

I tried to use the linux driver install script from the ATI website, but that threw an error as well:

```


will@linuxbox:~$ sudo ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


```

---

### Post by Crafty Kisses on 2007-06-18
> **Page said:**
> Envy produced the following output:

```

Envy Error: ATI's legacy driver does not support your operative system

```

Installing the ATI driver manually through envy created the same problem I described in the beginning of this thread. 

I tried to use the linux driver install script from the ATI website, but that threw an error as well:

```


will@linuxbox:~$ sudo ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install


```
You should try reconfiguring your X server file:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by badhorse on 2007-06-18
I have an ATi Radeon 9200SE and it works out of the box, but NO direct rendering. To enable direct rendering i should modified xorg.conf like follows:



Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Driver 		"radeon"
	BusID		"PCI:1:0:0"
	Option 		"BusType" "PCI"
	EndSection

Now i have direct rendering but Beryl running slow.

---

### Post by Kubunteando on 2007-06-18
What version of Ubuntu are you using?

Post your current xorg.conf file, so we can have a look and advice you.

Your card is not supported any more by ATI, so I think you have made the right choice to use the Open Source drivers (the radeon driver). The Open Soource drivers will be still supporting your card.

---

### Post by benamsee on 2007-08-23
Hi I do have the same problem but I don't get the "direct rendering" to "yes" with the "radeon" driver. Can anyone help me?

My xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
# 
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
# 
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
# 
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
# 
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg
# 
# File edited by xorg-edit v07.06.15 at Tue Aug 21 21:46:44 2007

Section "Files"
	# path to defoma fonts
	FontPath "/usr/share/fonts/X11/misc"
	FontPath "/usr/share/fonts/X11/cyrillic"
	FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath "/usr/share/fonts/X11/Type1"
	FontPath "/usr/share/fonts/X11/100dpi"
	FontPath "/usr/share/fonts/X11/75dpi"
	FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "ServerFlags"
	Option "AIGLX" "off"
EndSection

Section "Module"
	Load "bitmap"
	Load "dbe"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "record"
	Load "v4l"
	Load "vbe"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "de"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "ZAxisMapping" "4 5"
	Option "Buttons" "7"
EndSection

Section "InputDevice"
	Identifier "stylus"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "stylus"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier "eraser"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "eraser"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier "cursor"
	Driver "wacom"
	Option "Device" "/dev/input/wacom"
	Option "Type" "cursor"
	Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
	Identifier "ATI Radeon 6250"
	Driver "radeon"
	BusID "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier "Standardbildschirm"
	Option "DPMS"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Radeon 6250"
	Monitor "Standardbildschirm"
	DefaultDepth 24
	Option "MonitorLayout" "Auto,Auto"
	SubSection "Display"
		Depth 1
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "stylus" "SendCoreEvents"
	InputDevice "cursor" "SendCoreEvents"
	InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Extensions"
	Option "Composite" "0"
EndSection

Section "DRI"
	Mode 0666
EndSection
```

---

### Post by Waappu on 2007-08-25
> **benamsee said:**
> Hi I do have the same problem but I don't get the "direct rendering" to "yes" with the "radeon" driver. Can anyone help me?

Hi

See if this helps

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

and set AIGLX and Composite to true in xorg.conf

---

