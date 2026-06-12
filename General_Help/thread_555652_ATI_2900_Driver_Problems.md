---
title: "ATI 2900 Driver Problems"
date: 2007-09-20
forum: General Help
---

### Post by fppl on 2007-09-20
Hey everyone

First of all I will start with my specs:

Intel dual core with Ubuntu 64 bit (feisty fawn 7.04) and an ATI 2900XT. Other than that, if necessary, here are my other specs: 2gb memory, pci sound card, LG lcd (19"). I included those which I think might have *any* relation to the problem.

I recently downloaded the new ATI 8.41.7 driver for my 2900XT... I followed this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Only I replaced everything with the new driver name... And then after that didn't *exactly* work, I ran the .run file with sudo bash and then I went into the console and did aticonfig --initial.

Voila! It all worked.. So far so good...

But then I read somewhere that my hardware acceleration wasn't enabled (I know it *was* now but I didn't really know what I was doing and I thought it was disabled and I wanted to enable it..)

So I went into the Restricted Drivers manager and enabled the ATI driver in the repositories (without knowing I did) and then a few seconds after it finished installing I realized what it did and that I probably ****** it all up.

Then I uninstalled everything and set my xorg to the default configs... With the VESA driver... It worked... And still does if I do it... But whenever I try to install the ATI driver again (the same way) it all seems to work fine before I restart (meaning, it isn't actually working.. but the installation seems to have went all well) and then after the Ubuntu boot bar finishes loading I just get a flickering black screen that doesn't change... It stays black even after an hour.

It doesn't even tell me that my X is messed up so I can get into nano and edit it... It just shows nothing... So I revert to my LiveCD to re-edit xorg.conf back to VESA and it works...

My question is... What can I possibly do to get the 8.41.7 driver working again?

Please help! I don't want to reinstall everything just for this... I'm sure there is a way! (This is linux, there are no restrictions!)

_**THANKS!**_

---

### Post by fppl on 2007-09-20
Guys please... Really.. I really want to sort this out... Please.. Someone help

---

### Post by mali2297 on 2007-09-20
Have you tried everything here? (Including manual removal of drivers.)
> 
 Revert to Xorg driver

If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing

sudo dpkg-reconfigure xserver-xorg

and selecting the "ati" driver, or simply restoring the previous /etc/X11/xorg.conf file, if you made a backup.

You also need to remove the xorg-driver-fglrx or your manually installed drivers to get the 3D acceleration back, since it is provided by file /usr/lib/libGL.so.1.2 which belongs to libgl1-mesa package and which is moved to backup and replaced at the installation of xorg-driver-fglrx (or the manually built) package. In case the removal of the fglrx drivers fails to restore the file from libgl1-mesa, you have to reinstall the package by running:

sudo apt-get install --reinstall libgl1-mesa

and then installed the ATI 8.41.7 driver again.

---

### Post by fppl on 2007-09-20
Hmm... I did try reinstalling every thing after reverting to original... I will try that re-installing of that library and let you know.. Thanks!!!

---

### Post by fppl on 2007-09-20
Damn.. Didn't work... Are you saying that the only way to re install video drivers properly on Ubuntu is to reformat the whole system? I already have tons of stuff on this one (and it's not easy to back up programs since you have to take files from all these directories)..

Man I really don't wanna reformat my computer again. one thing I really don't get though is howcome anyone barely comes to this forum to help... Mostly I only see the ranting threads getting the help (when in the meanwhile people are telling them there is no need to get upset, here is how to do this and that) and all the other threads are getting ignored... The meaning of this distro's name is humanity towards others but I barely see people respond to the help threads... I know it's no one's real fault because no one *has* to help other people here... But still, since this is supposed to be the meaning of this distro it's annoying you know..

---

### Post by fppl on 2007-09-20
Might aswell post my xorg.conf video configs

```
Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
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

Section "DRI"
	Mode         0666
EndSection
```

---

### Post by angryfirelord on 2007-09-20
That's an old guide. Start at Method 2 for Feisty. 

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually")

---

### Post by fppl on 2007-09-20
Just tried that guide... It looked promising but it gave the same error!

What can I do to fix this??? Mind you it WORKED yesterday before I clicked the 'enable ati acceleration driver' on the restricted modules page. I'm sure someone here knows what was changed by that and thus knows how I can fix this... Come on I'm not asking for too much here. Just help me get my drivers back! I waited 4 months until they came out, then they worked and now I can't get them to work again! It's so frustrating!!!!

---

### Post by fppl on 2007-09-20
This is my xorg.conf

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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us,il"
	Option	    "XkbVariant" ","
	Option	    "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

My xorg-driver-fglx and the kernel driver for it are all updated according to Synaptic (8.41.7) ... The xorg.conf all works great when I just change fglrx to vesa, but then I am not using the driver... 

This means that the problem is likely not in the configs but more in the actual driver... Because the problem always happens only when I change back to fglrx.

The problem is: once the Ubuntu bar finished loading, the screen becomes black (it doesn't shut off, it just shows black) and after a few seconds it shuts itself off (gets really black) .. 
After a few seconds it goes back to show the 'on' black and then shuts down to total black again...

Maybe it has something to do with the kernel or something, looking for the hardware that the fglrx is looking for and not finding it... Does that make any sense at all?

I really want to fix this guys... I can't sleep or do anything until I fix this... My mind keeps focusing on it and it's already almost 4am here... PLEASE! someone help me here!

---

### Post by angryfirelord on 2007-09-20
I installed the fglrx drivers using that guide & it worked fine for me. If vesa works, then your xorg.conf should be ok.

I'm going to suggest the you uninstall the 8.41 drivers and remove every fglrx related package on your system (if you followed the guide, the ati installer generated 4 packages) and try it again. Make absolutely sure that fglrx is included in the DISABLED_MODULES & that you ran module-assistant. I know for a fact that the 2900 is supported under the 8.41 driver.

My suggestion is that you keep a log of the stuff you entered in the terminal and what comes out. (put it in a text file or something equivalent) Then, if it still doesn't work, post the contents of the text file. Since I was able to get it running, I still believe something went wrong in the installation process.

---

### Post by fppl on 2007-09-20
Here is pre-reboot (by the manual, I first need to reboot and THEN do aticonfig --initial)... Here's what I've done so far: (BTW I really appreciate your help, you're a life saver just by helping!!!!!)

```
root@yam-desktop:~# cp /home/yam/Folder/ati-driver-installer-8.41.7-x86.x86_64.run Desktop/ati-driver-installer-8.41.7-x86.x86_64.run
root@yam-desktop:~# cd Desktop        root@yam-desktop:~/Desktop# ls
ati-driver-installer-8.41.7-x86.x86_64.run
root@yam-desktop:~/Desktop# sudo bash ati-driver-installer-8.41.7-x86.x86_64.run --buildpkg Ubuntu/feisty
Created directory fglrx-install.wS5208
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.41.7...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/feisty
Package /root/Desktop/xorg-driver-fglrx_8.41.7-1_amd64.deb has been successfully generated
Package /root/Desktop/xorg-driver-fglrx-dev_8.41.7-1_amd64.deb has been successfully generated
Package /root/Desktop/fglrx-kernel-source_8.41.7-1_amd64.deb has been successfully generated
Package /root/Desktop/fglrx-amdcccle_8.41.7-1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.wS5208
root@yam-desktop:~/Desktop# gksu gedit /etc/default/linux-restricted-modules-common
root@yam-desktop:~/Desktop# sudo dpkg -i xorg-driver-fglrx_8.41.7-1*.deb \
> fglrx-kernel-source_8.41.7-1*.deb \
> fglrx-amdcccle_8.41.7-1*.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 139043 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.41.7-1_amd64.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.41.7-1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.41.7-1_amd64.deb) ...
Setting up xorg-driver-fglrx (8.41.7-1) ...
Starting atieventsd: done.

Setting up fglrx-kernel-source (8.41.7-1) ...
Setting up fglrx-amdcccle (8.41.7-1) ...

root@yam-desktop:~/Desktop# rm /usr/src/fglrx-kernel*.deb
root@yam-desktop:~/Desktop# module-assistant prepare
Getting source for kernel version: 2.6.20-16-generic
Kernel headers available in /lib/modules/2.6.20-16-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
root@yam-desktop:~/Desktop# module-assistant update 

Updated infos about 86 packages
root@yam-desktop:~/Desktop# module-assistant build fglrx
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.20-16-generic_8.41.7-1+2.6.20-16.31_amd64.deb .
root@yam-desktop:~/Desktop# module-assistant install fglrx
Selecting previously deselected package fglrx-kernel-2.6.20-16-generic.
(Reading database ... 139190 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.20-16-generic (from .../fglrx-kernel-2.6.20-16-generic_8.41.7-1+2.6.20-16.31_amd64.deb) ...
Setting up fglrx-kernel-2.6.20-16-generic (8.41.7-1+2.6.20-16.31) ...

root@yam-desktop:~/Desktop# depmod -a                     
root@yam-desktop:~/Desktop# mkdir /lib/modules/$(uname -r)/volatile
root@yam-desktop:~/Desktop# ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
root@yam-desktop:~/Desktop# 

```

---

### Post by fppl on 2007-09-20
After rebooting, I changed vesa back to fglrx (I already had the aticonfig --initial from before... no changes besides vesa) and the black screen of death popped out again... vesa still works.....

Did anything go wrong with the installation?

---

### Post by fppl on 2007-09-20
--

---

### Post by fppl on 2007-09-20
angryfirelord can you post your xorg.conf please?

---

### Post by fppl on 2007-09-20
Thought I might as well upload some logs from X.org....


Here's the log when using vesa:
[http://www.files.winupload.org/1190344160-vesa-xorg.log](http://www.files.winupload.org/1190344160-vesa-xorg.log)

Here's the problematic one when using fglrx...
[http://www.files.winupload.org/1190344287-fglrx-xorg.log](http://www.files.winupload.org/1190344287-fglrx-xorg.log)

Maybe the experts can figure this log out. :S All I got was that it needed X.org version 7.1.x.x to run this driver properly while x is larger than 0. Well my X.org is 1.7.2 last time I checked.... Maybe I should reinstall it? I foresee problems with the latter option though...

---

### Post by fppl on 2007-09-20
Interesting:
```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xd0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2b08ab48ed40]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxModeInit+0x43) [0x2b08ad4bf0c3]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxScreenInit+0x4a6) [0x2b08ad4be306]
4: /usr/bin/X11/X(AddScreen+0x222) [0x436652]
5: /usr/bin/X11/X(InitOutput+0x268) [0x465098]
6: /usr/bin/X11/X(main+0x275) [0x436e55]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b08ab47b8e4]
8: /usr/bin/X11/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting

```

Especially this part:

```
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
```

---

### Post by angryfirelord on 2007-09-21
Here's what I have:
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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI RADEON X1600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1917"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X1600"
	Monitor		"Acer AL1917"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
You may also want to re-run:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fppl on 2007-09-21
Yeah.. Ah the hell with it. I'm just gonna give openSUSE a shot heh... might work. (it's sponsored by AMD which own ATI so that might help somewhere hehe :p)

---

### Post by angryfirelord on 2007-09-23
Ok, I did a re-install of Ubuntu and ran into the same problem. I'm not exactly sure how I fixed it, but here are the last commands that I executed:
```
sudo aticonfig --initial
```
```
sudo depod -a
```
```
sudo mkdir /lib/modules/$(uname -r)/volatile
```
```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
```
```
sudo reboot
```
:confused: Weird, oh well.

---

