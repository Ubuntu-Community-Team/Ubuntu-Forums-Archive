---
title: "Xubuntu 7.10 display problems..."
date: 2007-11-27
forum: General Help
---

### Post by andre-w on 2007-11-27
Hello again!

I was running Xubuntu 7.04 (Feisty Fawn) on my Toshiba laptop until a couple of weeks ago when I tried to upgrade to Xubuntu 7.10 (Gutsy Gibbon). In order to do that I used the Software Updates option... first Gutsy was downloaded, then installed, and finally the system rebooted, but after the initial boot logo (with the progress bar) the screen went blank. I waited a while and then reset my laptop, and the same happened again. I even tried booting with an external monitor... same thing. It seems to me that it stopped either right before or actually on the login screen.

Later I tried booting on recovery mode and it worked, however I find myself in the command-line mode and I have no idea on what to do next, and when I try to run Xfce the screen goes blank again. I also tested booting with Xubuntu Live CDs... 7.04 (FF) CD works and I can see my files, but 7.10 (GG) CD shows only the boot logo and then goes blank.

My first thought was to backup my files and fresh-install ol' Feisty, but as a result I would loose all customization, and moreover, I cannot understand why my laptop is not able to run the newest Xubuntu. My Toshiba Satellite has a Celeron 800 MHz, and 384 MB (6 times the minimum and 3 times the recommended).

Any help will be welcome. Thanks in advance!

Andre W.

---

### Post by Sef on 2007-11-27
What is your graphics card?

---

### Post by andre-w on 2007-11-27
Hello Sef!

The Toshiba Support web-page for my Satellite 1800-S203 says I have a Trident graphics controller (8MB external UMA video memory).

More info can be found at (click on Detailed Specs):
[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modelLanding.jsp?moid=1073833650](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modelLanding.jsp?moid=1073833650)

---

### Post by andre-w on 2007-11-28
I have been reading a lot and ended up experimenting with a couple of tricks... here are my findings:

I booted on recovery mode, opened /boot/grub/menu.lst and played with "splash" and "nosplash" parameters, but the outcome is the same... after the splash screen with the progress bar (or the otherwise text-mode boot sequence) I see a blinking "_" for one or two seconds and then the screen goes blank.

I also tried hitting Alt+F1 and Ctrl+Alt+F1 when I see the "_" blinking... it quickly asks me for my username, but then I get the black screen before I could type the first letter.

I even reviewed /etc/usplash.conf and the resolution was matching ( 1024x768 ), and I updated the splash theme just in case (sudo update-usplash-theme usplash-theme-xubuntu)... no difference.

Does anyone know what is happening here?

---

### Post by andre-w on 2007-11-30
I would really appreciate any piece of advice available from the community. The fact is... I don't have a clue. If someone have a hint of what is going on here, even though it is only a tip, please... your suggestions are more than welcome.

Regards

---

### Post by NT4usB on 2007-11-30
Not sure...
Couple guesses though.
Boot to grub. cd into /etc/X11/ and edit xorg.conf change the driver to vesa and look at/fix resolutions and refresh rates.
Boot to the live CD. mount your HDD. Edit xorg as above.

---

### Post by siuishere on 2007-11-30
Same thing here with the same Laptop Model.

Ubunto, Kubunto and Xubuntu did not start up. Only the blinking prompt is shown at the screen.

Please Help :(

---

### Post by andre-w on 2007-11-30
Hello NT4usB,

Thanks for the new information!

I shall study and test it as soon as possible, and post the results here.

---

### Post by andre-w on 2007-11-30
Hello siuishere,

Same laptop model, what a coincidence! But it seems to me we are not alone... looking at the Ubuntu Forums alone, I noticed the problem we are experiencing has been a headache for a lot of people using other laptop brands. I also realized this issue is a 7.10 version bug, now being addressed by the development team.

I am assuming you are trying to install the new Gutsy, but out of curiosity, have you ever tried to install previous Ubuntu/Kubuntu/Xubuntu versions? And maybe most importantly, is your boot sequence behaving exactly like mine (with the black screen after a quick blinking "_" prompt), or is it slightly different (frozen with the prompt blinking endlessly)? If possible, please post more specifics.

You might want as well to read and subscribe these other threads I found in the Forum:

[http://ubuntuforums.org/showthread.php?t=623037](http://ubuntuforums.org/showthread.php?t=623037)

[http://ubuntuforums.org/showthread.php?t=579684](http://ubuntuforums.org/showthread.php?t=579684)

[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

I will be doing the same...

---

### Post by andre-w on 2007-12-02
So first I tried to find out more details about my video hardware...

The Toshiba Support web-page reads that the "*internal display supports up to 16M colors at **1024 x 768***", and "*External Color Support*" is:

[I]640 x 480; 85Hz Non-Interlaced @ 16M
800 x 600; 85Hz Non-Interlaced @ 16M
1024 x 768; 85Hz Non-Interlaced @ 64K
1280 x 1024; 85Hz Non-Interlaced @ 64K
1600 x 1200; 60Hz Non-Interlaced @ 64K[/I]

I also learned that my graphics card is the "*Trident CyberBlade Ai1*" by reviewing the Downloads page (knowing that those were files for Windows 98, Me and 2000).

And before I began changing things, I tried one trick I learned, **sudo ddcprobe**, and here is the output:

```
vbe: VESA 2.0 detected.
oem: Trident CYBER 8620
memory: 8192kb
mode: 1280x1024x64k
mode: 1280x1024x32k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 640x480x16m
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 800x600x32k
mode: 800x600x64k
mode: 640x480x32k
mode: 640x480x64k
mode: 1024x768x256
mode: 1280x1024x16
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x16
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x60 (text)
mode: 80x60 (text)
mode: 800x600x16
edid: 
edid: 1 3
id: 5082
eisa: TOS5082
serial: 00000000
manufacture: 0 1990
input: analog signal.
screensize: 27 21
gamma: 1.000000
dpms: RGB, no active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@75 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
ctiming: 1280x1024@60
ctiming: 1600x1200@60
dtiming: 1024x768@0
monitorname: TOSHIBA Inte
monitorname: rnal 1024x76
monitorname: 8 Panel
```

Then, following the suggestions given by NT4usB, I booted Gutsy on recovery-mode and opened **/etc/X11/xorg.conf** in order to fix resolution and refresh rates.

Here is the original file:

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
	Identifier	"Trident Microsystems CyberBlade/i1"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade/i1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

And here are my changes:

```
Section "Device"
	Identifier	"Trident Microsystems CyberBlade/i1"
#	Driver		"trident" # OLD
	Driver		"vesa" # NEW
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51 # Refresh rate?
	VertRefresh	43-60 # Refresh rate?
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade/i1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Option		"metamodes" "1024x768_85 +0+0" # NEW
```

On the last line I tried **1024x768_85** and **800x600_85**, as well as **1024x768_87** and **800x600_72** (taking in account the ddcprobe output), but all theses options did nothing to solve my problem. After that I changed back to the original settings. I was wandering if _HorizSync _and _VertRefresh_ are refresh rate parameters, but I would not know how to translate rates onto those ranges (*28-51* and *43-60* respectively).

No positive outcome so far... I will keep on troubleshooting and counting on more input from the community.

Thanks in advance!

---

### Post by CPtAJ on 2007-12-07
I'm not sure how you're going to do it but try booting with xfbdev instead of xvesa. I recall xvesa giving me problems when I installed Damn Small Linux on an older laptop screen. At any rate, its worth a shot since everyone seems to be out of ideas here.

---

### Post by andre-w on 2007-12-07
Thank you, CPtAJ !

Your ideas are very welcome!

But the fact is... I'm sailing uncharted waters! xfbdev? xvesa? Are they parameters or packages? Not quite sure what they are... but I'll figure them out, and then report back.

Best regards,

Andre W.

---

### Post by andre-w on 2007-12-13
Hi CPtAJ ! I appreciate your contribution... however, I still could not solve this puzzle.

I have been reading other threads as well, but the more I read, the more a get confused... and discouraged. I am now pondering over downgrading back to Feisty... it seems to be the only way out, unless someone out there knows how to fix that flaw.

Is it possible to downgrade from Gutsy to Feisty keeping all my user's documents, settings and installed packages?

Thanks in advance.

---

