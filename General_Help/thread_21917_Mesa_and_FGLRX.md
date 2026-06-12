---
title: "Mesa and FGLRX"
date: 2005-03-24
forum: General Help
---

### Post by DuplexEmotions on 2005-03-24
I know this has been addressed several times, and I have gone through most of the other threads looking for a response and have come up short with my specific problem.

First, specs and backstory. I'm reletively new to linux but good with electronics in general, was running Warty and after I replaced my motherboard reinstalled with Hoary. the comp is:
Ath XP 2500+ @stock speeds for the moment
Shuttle AN35N-Ultra motherboard
1gb Mushkin PC-3500 @ 5-3-3-6
ATI Radeon 9700 Pro
Creative labs Audigy
and 2x120gb Western Digital hard drives (IDE)

the problem I am having is that the mesa OpenGL drivers are loaded and for some reason I can't get it to switch to the ATI drivers. I kinda need 3d accelleration, so this needs to be addressed ASAP. Here's my xorg.conf file.

---------------------------------------------------------------

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ MV720"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Monitor		"COMPAQ MV720"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
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
--------------------------------------------------------------------

This is all running on one single monitor, by the way.

Thanks for all the help (you've all been a major help when I was lurking before i made an account). I'll be checking this all day, if you have any questions just ask and I will address them as best i can.

---

### Post by robtotheb on 2005-03-24
I have the same problem with my 9700pro card.  I have read through ALL the posts (trying the different suggestions) on this subject and none of them helped! 

I type in fglrxinfo and still get...

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

and my xorg.conf is ....

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"DPRO750SB"
	HorizSync	30-96
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Monitor		"DPRO750SB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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




SOMEONE PLS HELP THIS IS GIVING ME A HEADACHE!!

---

### Post by bobmitch on 2005-03-24
Changing the driver to 'fglrx' from 'ati' or 'radeon' will not always work.

Use the 'fglrxconfig' tool (which is installed with the fglrx packages) to create the appropriate config file which will have a much higher probability of providing hardware accelerated opengl.

NB.  The fglrxconfig file will generate an xfree config file - but as long as you rename/remove the existing xorg.conf, it xorg will fall back to using an xfree config file.

---

### Post by robtotheb on 2005-03-24
I have tried 'fglrxconfig' in warty before and ended up breaking the graphics driver completely and had to re-install Ubuntu.   [-o<

---

### Post by emperor on 2005-03-24
Is the fglrx driver loaded?

The "flgrx" module MUST be loaded manually in "/etc/modules".

Check using "lsmod" in a terminal session.

---

### Post by robtotheb on 2005-03-24
Just tried it - doesn't work - same result.  The config files are exactly the same

---

### Post by alastair on 2005-03-24
A tip :

If you play with X11 config files (either editing or via a tool like "fglrxconfig"), make a BACKUP copy. In fact, if you have a working config - make a backup anyway. No need to reinstall the OS!

Why don't people look in the X logs and see what's going on? This is where warnings and errors get printed e.g.

/var/log/Xorg.0.log

---

### Post by robtotheb on 2005-03-24
I do back stuff up now...

and "people" don't look in X logs because they didnt know about them!

---

### Post by DuplexEmotions on 2005-03-24
i've tried using the fglrxconfig to make an XFree86 file and moved my xorg.conf file, and now the video doesn't work as well as it did when i was using the xorg file. fireglcontrol reads it as the ATI drivers not being installed. I'll continue plodding around with it, maybe reinstall fglrx and see if that helps.

I love ubuntu, I just wish it was more happy around ATI.

Edit:
And not to be rude to whomever made the comment on reading log files, the people having these problems are usually the linux novices. Browsing through log files can often lead to confusion rather than help, as they are not always easy to interpret if you do not know what to look for. Just need to be understanding about it all.

---

### Post by Dracontopes on 2005-03-24
Try this:

Run fglrxconfig again. When asked to use external AGPGART module/blablabla, don't answer [n] (default) but answer yes (y).

I had the same problem, this fixed the problem. Don't forget to restart X :D (and follow instructions to copy the XF86Config-4 file to xorg.conf :))

(sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup)
(sudo cp /etc/X11/XF86Config-4 /etc/X11/xorg.conf)
(startx)

---

### Post by bobmitch on 2005-03-25
There is always the option of installing the latest binaries from ati directly.
They are an order of magnitude better than the drivers supported by ubuntu.

---

### Post by alastair on 2005-03-25
I have re-read what I wrote "Why don't people look in the X logs and see what's going on?", and don't think I was being rude. I certainly did not mean to be. The point was to highlight where to look for X problems. 

I would not expect people to understand what is in the log file - but posting the messages here would let others have a look and perhaps spot a problem. It's still a good idea.

---

### Post by robtotheb on 2005-03-25
Dracontopes I've tried what you said I cant start up Xserver.  However if i remove xorg.conf and let ububutu defualt to XF86Config-4 then Xserver loads but 3D still doesnt work and fglrxinfo still outputs mesa drivers.  But something changed as I can change resolutions now and my mouse wheel doesnt scroll #-o  (it annoyed me so I restored the xorg.bak)

I have attached my log as a .txt file but its actaully a .tgz  (was too large to attach unzipped!)

Thanks

---

### Post by alastair on 2005-03-25
Looking at your log file, the following stands out :

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"

So - AGP is failing and so DRI (direct rendering) fails to initialise.

Looking on the web - google search for : 

   unable to acquire AGP, error "xf86_ENOMEM" xorg fglrx
   
Gives some leads e.g.

[http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#4_agpenomem](http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#4_agpenomem)

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)
  - section "2.2. AGP support"
  

i.e.

"The error unable to acquire AGP, error "xf86_ENOMEM" in your XFree86
log usually means that you are using the built-in AGP support with an
unsupported chipset. Set "UseInternalAGPGART" to "no" and load the
kernel driver (see below for details) which will hopefully support
your AGP chipset."

and 

- Increase your AGP aperture size in the BIOS (particularly for
  nForce2 boards)
- If you have an nForce2 board, try disabling the "AGP 8x Support"
  option in the BIOS.
- Check that you haven't set "UseInternalAGPGART" to "yes" and have
  your kernel AGP settings compiled in (this won't work)
- Set "UseFastTLS" to "2" in your XF86Config/xorg.conf file.
- Check the output of the "dmesg" command for errors.
- Check that your kernel configuration is correct.
- Try a newer kernel version.

Check the output of "dmesg" - and see what AGP messages might be in
there.


So .... BACKUP the /etc/X11/xorg.conf (make a copy)

And look to try (in the "Device" section with "fglrx") :

  Option "UseInternalAGPGART" "no"

This will require you to LOAD an AGP module before X starts i.e.

  modprobe agpgart
  modprobe via-agp (or whatever)
  
To find AGP modules : find /lib/modules/`uname -r` -name '*agp*'


and/or

  Option "AGPMode" "4"

But take a look at the web pages and see if you get anywhere.

---

### Post by Dracontopes on 2005-03-25
[QUOTE=robtotheb]Dracontopes I've tried what you said I cant start up Xserver. However if i remove xorg.conf and let ububutu defualt to XF86Config-4 then Xserver loads but 3D still doesnt work and fglrxinfo still outputs mesa drivers. But something changed as I can change resolutions now and my mouse wheel doesnt scroll #-o  (it annoyed me so I restored the xorg.bak)

I have attached my log as a .txt file but its actaully a .tgz  (was too large to attach unzipped!)

Thanks[/QUOTE]
 Yes, when I let fglrxconfig make a configuration file, I rename it to xorg.conf and edit it with

sudo vi /etc/X11/xorg.conf

Oh and don't forget this:    Option "UseInternalAGPGART" "no"
Important!

I have to change the keyboard driver from "Keyboard" to "keyboard" everytime I make a new config file :(

**Update:**

I had troubles AGAIN with fglrx module etc, but I found a nice guide that actually WORKED!

Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=18061&highlight=FATAL%3A+Module+fglrx](http://www.ubuntuforums.org/showthread.php?t=18061&highlight=FATAL%3A+Module+fglrx)

Important part:

> 
 1. Download official driver .rpm from the ATI website.
 2. Remove fglrx packages using synaptic.
 3. Shut down gnome. [ From terminal: sudo /etc/init.d/gdm stop ]
 4. cd to where you downloaded the driver rpm file.
 5. sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm
 6. sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
 7. dpkg --force-overwrite -i fglrx_6_8_0-8.10.19-1.i386.deb
 8. cd /lib/modules/fglrx/build_mod
 9. sudo sh make.sh
 10. cd /lib/modules/fglrx
 11. sudo sh make_install.sh
 12. modprobe fglrx
 13. fglrxconfig


---

### Post by robtotheb on 2005-03-26
This is madness - tried some of the things above and no luck.  What a joke of a driver....  last time i buy ati!  Thanks for the help  ](*,)

---

### Post by DuplexEmotions on 2005-03-27
[QUOTE=alastair]I have re-read what I wrote "Why don't people look in the X logs and see what's going on?", and don't think I was being rude. I certainly did not mean to be. The point was to highlight where to look for X problems. 

I would not expect people to understand what is in the log file - but posting the messages here would let others have a look and perhaps spot a problem. It's still a good idea.[/QUOTE]

I understand, sorry for being a bit of a jerk. I used to work as a PC repair tech so I'm used to seeing a lot of people get upset over similar things. I'll post my log file if trying those steps Dracon posted doesn't work.

---

