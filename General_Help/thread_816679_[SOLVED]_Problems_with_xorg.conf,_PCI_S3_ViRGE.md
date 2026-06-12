---
title: "[SOLVED] Problems with xorg.conf, PCI S3 ViRGE"
date: 2008-06-02
forum: General Help
---

### Post by Dr.Ninethousand on 2008-06-02
I can't get this old Virge to work, a regular boot up leaves me at a GUI advising me that I'm in low graphics mode, and a utility to configure my graphics, which doesn't seem to work ('test' and 'save' buttons don't do anything).  Furthermore, these commands don't seem to actually change my xorg.conf:

sudo dpkg-reconfigure -phigh xserver-xorg
sudo X -configure
sudo dpkg-reconfigure xserver-xorg

after running these, xorg.conf still just looks like:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

If you can't help with this, then maybe you can suggest a brand/model of video card for an older (1998) system with PCI slots..

---

### Post by NT4usB on 2008-06-03
I have one here I just installed Hardy on. Let me dig it out of the closet, fire it up, and post the xorg. And, yes... it royally sucked trying to get it to work. Hardy couldn't make it work beyond vga so I had to do a custom xorg.

---

### Post by Dr.Ninethousand on 2008-06-03
thanks NT4usB, I would really appreciate that..

---

### Post by NT4usB on 2008-06-04
oops... It's not a virage but it uses the virge driver.
Best I can get out of it is 1400x1050 @ 60 Hz for my Viewsonic VX2035wm

Be sure to set the resolution, refresh, etc., appropriate to your display.

01:00.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (rev 02)

```
ct@piii550:~$ cat /etc/X11/xorg.conf
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
EndSection

Section "Device"
	Identifier	"s3trio"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"s3virge"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"vx2035wm"
	Vendorname	"Viewsonic"
	Modelname	"Viewsonic vx2035wm"
	Gamma	1.0
	HorizSync	30.0 - 82.0
	VertRefresh	50.0 - 85.0
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"s3trio"
	Monitor		"vx2035wm"
	Defaultdepth	16	
	SubSection "Display"
		Depth	16
		Modes	"1600x1050_60" "1600x1200_60" "1400x1050_75" "1280x1024_72" "1024x768_85" "800x600_85" "640x480_85"
		Depth	24
		Modes	"1600x1050_60" "1600x1200_60" "1400x1050_75" "1280x1024_72" "1024x768_85" "800x600_85" "640x480_85"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by Dr.Ninethousand on 2008-06-04
sorry, no good..  I also booted up knoppix, which worked with the card right away, and copied info from the xorg.conf there, but that didn't seem to change anything..

---

### Post by doorknob60 on 2008-06-04
OH god, I hate that bug where you xorg won't configure properly with sudo dpkg-reconfigure xserer-xorg. I'd *really* like to see a solution here. It happens in Debian too, but I think Ubuntu might have added that feature (meaning it's not supposed to be in Debian), but I've seen it in Ubuntu too, and it's a major PITA. Anyone have a solution? EDIT: Wow that's an ancient card, i had it on my computer from 1997 with 32 Mb of ram and a 300 mhz processor lol.

---

### Post by NT4usB on 2008-06-04
The Trio is in a PIII 550 w/768mb of PC100 on a Intel SE440BX board. 'bout 1998 vintage.
I have a zesty Matrox Millennium in a PIII 733 that flies! 8mb of memory on that puppy.

What I hate about Hardy is instead of x blowing up, it reverts to a failsafe x... and fills .../X11/ with copy after copy of broken xorg.confz.
I had twenty-one to delete once I got this working.

btw, dpkg-reconfigure -phigh worked for me and got me closer to the working xorg... which is to say, got me past the failsafe. From there, just a matter of tuning to get the resolution, etc.
...and remembering to rename a copy before restarting x so I don't have to search through the dozens of failed copies to undo the last change and try again.

Ubuntu is getting more windows-like with every new release. Soon, we'll be having to answer that obnoxious *Are You Sure...?* popup whenever we make a change.

---

### Post by Dr.Ninethousand on 2008-06-04
Well I've installed Debian on this machine now instead, and it gave me a normal looking xorg.conf, but 640x480 is still the only option I'm given, even after removing it from xorg.conf.  Any ideas?

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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"S3 Inc. ViRGE/DX or /GX"
	Driver		"s3virge"
	BusID		"PCI:0:9:0"
EndSection

Section "Monitor"
	Identifier	"DELL M992"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. ViRGE/DX or /GX"
	Monitor		"DELL M992"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by NT4usB on 2008-06-04
Change the default depth to 16.

---

### Post by Dr.Ninethousand on 2008-06-04
no change..

---

### Post by NT4usB on 2008-06-05
Add the refreshes and freqs:
```

Section "Monitor"
	Identifier	"DELL M992"
	HorizSync	30.0 - 96.0
	VertRefresh	50.0 - 160.0
	Option		"DPMS"
EndSection

...
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_75" "1024x768_75"
	EndSubSection
...
```

---

### Post by Dr.Ninethousand on 2008-06-06
I installed Debian and at least got a xorg.conf with some content..  but I ended up getting somewhere by setting the driver to "vesa"..  then while reinstalling Ubuntu it crashed and I couldn't fix dpkg..  the CPU is 500MHz and it runs awful, and a new-used 1.4GHz cpu should be in the mail any day now so I'm waiting for that to try again..

anyway I expect my Debian generated xorg.conf with vesa modification to get me where I need to be..

still I would very much like to see Ubuntu's xorg configuration problems fixed..

---

### Post by Dr.Ninethousand on 2008-06-06
back in xubuntu now, and found that the vesa driver didn't play video any better than the integrated video chip does..  so with some more messing around I have the s3virge driver working and looking fairly good and playing videos..

but now I find that when I try to run xfce4-terminal, X crashes and restarts..  I can see the terminal open for a split second before X crashes..

thanks for your help with all this..

---

### Post by Dr.Ninethousand on 2008-06-06
apparently the crash is a known issue and is 'solved' by changing the default color depth from 24 to 16, or lower..


oh and by the way, that new-used cpu I got wouldn't start up..  I suppose the fsb was too fast or something..  :(

so I may end up having to get a better video card anyway just to make this thing reasonably useful..

---

### Post by Shismaeroth on 2008-08-08
Try this :

1)launch "kcmshell"

go to Hardware, choose your graphic card and monitor model
click on test, it will create  a xorg.conf.failsafe file in your /etc/X11/ directory

2)rename xorg.conf.failsafe -> xorg.conf
3)kill your X server and launch "startx"

4)launch "gnome-display-properties"

choose the desired resolution...


be careful s3 drivers are strange under ubuntu, in my computer
a 1024x768 with 87hz resolution seems to be stable with my S3 Virge DX, with other frequencies, some stripes appear when I move the mouse !

here is my xorg.conf:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"S3 ViRGE/DX (generic)"
	Busid		"PCI:0:9:0"
	Driver		"s3virge"
	Screen	0
	Vendorname	"S3"
	Videoram	8192
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Iiyama"
	Modelname	"Iiyama A705MT, VisionMaster Pro 411 /i70A"
	Horizsync	30.0-86.0
	Vertrefresh	50.0-180.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@85"	"640x480@85"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@85"	"640x480@60"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1024x768@43"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x960@85"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"	"1856x1392@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

-------------------------

Hoping it could help ^^

(Excuse for my crappy english/american but i'm french)

---

### Post by Scunge on 2008-08-27
I have similar problems with an old S3 display card (Windows identifies it as an "*S3 Trio 32/64*").

It doesn't scroll window contents properly if I use the automatically-setup "s3" in xorg.xonf, and as suggested by some other topics here I had to change the driver to "vesa" and 16 bit colour depth to get anything usable. Even then, it's soooo slow even on a 700 MHz machine, you can see it drawing every part of every window.

However, in trying to follow Shismaeroth's advice in the above post, I'm afraid I don't get very far at all!

> launch "kcmshell"
I get the following:
```
$ kcmshell
The program 'kcmshell' is currently not installed.  You can install it by typing:
sudo apt-get install kdelibs4c2a
bash: kcmshell: command not found

$ sudo apt-get install kdelibs4c2a
[...]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdelibs-data libarts1c2a libartsc0 libavahi-qt3-1 liblua50 liblualib50
  libqt3-mt
Suggested packages:
  fam perl-suid libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql
Recommended packages:
  libarts1-akode
The following NEW packages will be installed
  kdelibs-data kdelibs4c2a libarts1c2a libartsc0 libavahi-qt3-1 liblua50
  liblualib50 libqt3-mt
[...]
Get: 1 http://gb.archive.ubuntu.com hardy-backports/main kdelibs-data 4:3.5.10-0ubuntu1~hardy1 [7326kB]
Get: 2 http://gb.archive.ubuntu.com hardy-backports/main libartsc0 1.5.10-0ubuntu1~hardy1 [15.7kB]
Get: 3 http://gb.archive.ubuntu.com hardy/main libqt3-mt 3:3.3.8-b-0ubuntu3 [3299kB]
Get: 4 http://gb.archive.ubuntu.com hardy-backports/main libarts1c2a 1.5.10-0ubuntu1~hardy1 [1071kB]
Get: 5 http://gb.archive.ubuntu.com hardy/main libavahi-qt3-1 0.6.22-2ubuntu4 [33.4kB]
Get: 6 http://gb.archive.ubuntu.com hardy/main liblua50 5.0.3-3 [48.7kB]       
Get: 7 http://gb.archive.ubuntu.com hardy/main liblualib50 5.0.3-3 [35.1kB]    
Get: 8 http://gb.archive.ubuntu.com hardy-backports/main kdelibs4c2a 4:3.5.10-0ubuntu1~hardy1 [9614kB]
[...]
Selecting previously deselected package ...
Unpacking ...
[All did this with no other messages shown]

Setting up ...
[All did this with no other messages shown]

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

$ kcmshell
kbuildsycoca running...
Usage: kcmshell [Qt-options] [KDE-options] [options] module 

A tool to start single KDE control modules

[List of options excluded]

$ kcmshell --list
kbuildsycoca running...
Reusing existing ksycoca
The following modules are available:

$ 


```

I've left in certain package information so you can see exactly what was installed.

What exactly is the *kcmshell* command you are suggesting is run?

Thanks in advance.

---

### Post by Scunge on 2008-08-29
Some additional information...

I've just discvovered the command *lshw*, so here's the output from it for the S3 card:
```
        *-display
             description: VGA compatible controller
             product: 86c764/765 [Trio32/64/64V+]
             vendor: S3 Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller
             configuration: driver=s3fb latency=0 module=s3fb


```

Thanks for any help with this.

---

