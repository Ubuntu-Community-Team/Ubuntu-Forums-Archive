---
title: "screen resolution"
date: 2004-11-12
forum: General Help
---

### Post by redeye on 2004-11-12
Hi,  I'm new to Ubuntu and so far I had a great  experience with it.  Before I was using Fedora Core 2 which is a pretty good distro too but what i dont like about it is that it install too much s**t, instead ubuntu installs whatever is necesary for a pretty stable operating system. The only problem I got was with the screen resolution which let me use up to 1280x1024; it doesnt bother me but when I was using Fedora I was able to set it up to 1600x 1200. I'm using the default driver (VESA) and all the specifications of my monitor are correct on the xf86config file. Do I need  to update the driver? or perhaps xfree? Thanx in advance....

ooo, one more thing, everytime i reboot or boot my machine ,  before getting the loggin screen something weird happens, it seems to show a screenshot of the last thing that i was running, for example, after rebooting windows and choosing Ubuntu from LILO, a screenshot of the logging out of windows appears.... Does anybody had this problems before??

---

### Post by Magneto on 2004-11-12
[QUOTE=redeye]Hi,  I'm new to Ubuntu and so far I had a great  experience with it.  Before I was using Fedora Core 2 which is a pretty good distro too but what i dont like about it is that it install too much s**t, instead ubuntu installs whatever is necesary for a pretty stable operating system. The only problem I got was with the screen resolution which let me use up to 1280x1024; it doesnt bother me but when I was using Fedora I was able to set it up to 1600x 1200. I'm using the default driver (VESA) and all the specifications of my monitor are correct on the xf86config file. Do I need  to update the driver? or perhaps xfree? Thanx in advance....
[/QUOTE]

The version of XFree86 you are using with Ubuntu is not the same as with Fedora.  You should try to configure X for your specific video card, that generally provides for a better experience.

type this in a terminal
```
lspci 
```

and reply with what it tells you.

---

### Post by redeye on 2004-11-12
ok, this is the output i got :
k@kbox:~ $ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
It's an onboard video card.

---

### Post by Hairyharry on 2004-11-12
Check out [http://www.ubuntuforums.org/showthread.php?t=3700](http://www.ubuntuforums.org/showthread.php?t=3700). Had my problems sorted in less than 5 mins.

---

### Post by Magneto on 2004-11-12
[QUOTE=Hairyharry]Check out [http://www.ubuntuforums.org/showthread.php?t=3700](http://www.ubuntuforums.org/showthread.php?t=3700). Had my problems sorted in less than 5 mins.[/QUOTE]

thanks harry - 

Redeye - go with Harry's advice - 
 that driver on that page he linked is for your VIA KM400 chipset's embedded video
try to remember that you have that VIA KM400 because it will come up again if you try to configure your kernel or do some other things with your system

---

### Post by redeye on 2004-11-12
I followed the instructions on [http://www.ubuntuforums.org/showthread.php?t=3700](http://www.ubuntuforums.org/showthread.php?t=3700) but i still dont get the 1600x1200 resolution, though the problem with the weird screenshots was solved. I dont know what could be the problem, my monitor is a SyncMaster 955df; the specs are in [http://www.samsungusa.com/cgi-bin/nabc/product/b2c_product_detail.jsp?prod_id=AN19JSBLQ](http://www.samsungusa.com/cgi-bin/nabc/product/b2c_product_detail.jsp?prod_id=AN19JSBLQ). As i said before the gonfiguration for the monitor in Xf86config are correct. Any other ideas??

---

### Post by Magneto on 2004-11-12
> **redeye]I followed the instructions on [http://www.ubuntuforums.org/showthread.php?t=3700](http://www.ubuntuforums.org/showthread.php?t=3700) but i still dont get the 1600x1200 resolution, though the problem with the weird screenshots was solved. I dont know what could be the problem, my monitor is a SyncMaster 955df said:**
> http://www.samsungusa.com/cgi-bin/nabc/product/b2c_product_detail.jsp?prod_id=AN19JSBLQ[/url]. As i said before the gonfiguration for the monitor in Xf86config are correct. Any other ideas??
Please post your XF86Config-4

---

### Post by redeye on 2004-11-12
# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
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
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	HorizSync	30-85
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by TravisNewman on 2004-11-12
First off, in your screen modes, you don't have 1600x1200 listed. 
Second, do you know that the vertical refresh rate is what you have listed under the monitor section? If you have a manual, check it out and see, since the webpage on samsung's site didn't have it. If it can go higher, it might be able to get higher resolutions.

But if you add 1600x1200 to the config for all the depths you want to use (or at least for 24), that should get you going. If it doesn't work out, ctrl+alt+F1 to go to command line and edit the config again and take out the 1600X1200s

---

### Post by poptones on 2004-11-12
FWIW I had a similar issue with my Nvidia system. I have a Compaq MV940 which was properly detected, but after install it only gave me 1280x1024 resolution. No higher resolution options are offered in the config file for some very odd reason -  It was easy enough to fix, but it seems odd not to offer the higher resolutions when the hardware will handle it.

---

### Post by redeye on 2004-11-12
lol, I should've tried to add 1600x1200  to the modes before making suck a big deal of the resolution. thanx  panickedthumb... anyways it is weird that the maximun resolution that shows up is 1280x1024 when just installed...now I'm looking forward for the next version of ubuntu (hoary), i think it's time to get rid of winxp  from my machine, I haven't use it since I got fedora and now with ubuntu in my box I wont see Windows for the rest of my life , lol.  thanx everybody

---

