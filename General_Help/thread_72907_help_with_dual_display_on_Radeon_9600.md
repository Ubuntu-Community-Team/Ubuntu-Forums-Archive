---
title: "help with dual display on Radeon 9600"
date: 2005-10-07
forum: General Help
---

### Post by JakeSpeare on 2005-10-07
Hi all,

Just installed 5.04 on my box.  Would like to get dual display working (ie. one large desktop spanning my two samsung lcd's)  I have been scouring the forums to find the solution and have modified my xorg.conf a number of times, without avail.  It currently looks like this:


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
	Identifier	"Radeon 9600"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Radeon 9600"
	Monitor		"Monitor0"
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

Section "Screen"
	Identifier "Screen1"
	Device "Radeon 9600"
	Monitor "Monitor1"
	DefaultDepth 24
	Subsection "Display"
		Viewport 0 0
		Depth 24
		Modes "1600x1200"
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	Screen		0 "Screen0" LeftOf "Screen1"
	Screen		1 "Screen1" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "on"
	Option "Clone" "off"
EndSection



What am I missing?

:confused:

---

### Post by mlomker on 2005-10-07
I'll qualify this statement by saying that I've never done this, but there is a 'Virtual' command that can go into the display section...perhaps that's a part of the answer.

```

Subsection "Display"
     Depth 24
     Modes "1280x800"
     Virtual 1280 800
EndSubsection

```

---

### Post by JakeSpeare on 2005-10-07
I will try that.  Do you think it has anything to do with the fact that I am using the ati drivers that were installed during the ubuntu install?  Should I change them to anything else?

---

### Post by mlomker on 2005-10-07
> I will try that.  Do you think it has anything to do with the fact that I am using the ati drivers that were installed during the ubuntu install?  Should I change them to anything else?

I think I found the real answer, [here]("http://gnuman.com/guides/the_chronicles_of_x_part_3,_dual_display.html") and [here.]("http://72.14.203.104/search?q=cache:cr6qnGiobm0J:www.linux-magazine.com/issue/17/DualHead.pdf+%22dual+display%22+xfree+config&hl=en&client=firefox")  The virtual panning is to pan on a single display.  What you need is the Serverlayout section mentioned in these articles.

The Hoary drivers are old and slow.  I have a [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") for updating them if you prefer.

---

### Post by mcduck on 2005-10-07
no, the virtual thing makes your desktop larger than your monitor is, so that everything is not seen at one time, and moving mouse to the edge of screen pans your desktop.

It has nothing to do with dual screens.

edit. Too slow.. But it's good that you found the answer :)

---

### Post by JakeSpeare on 2005-10-07
I got it working!

Bizarre really.  I added a "virtual" device to deal with the other "head".  Got great dual display action now.  Will upgrade drivers when i get some time!

Thanks for all your help!

Here is my xorg.conf file for reference purposes (it is quite generic so should work for others, with minimal modification):


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
	Identifier	"videocard0"
	Driver		"ati"
EndSection

Section "Device"
	Identifier	"videocard1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"videocard0"
	Monitor		"Monitor0"
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

Section "Screen"
	Identifier "Screen1"
	Device "videocard1"
	Monitor "Monitor1"
	DefaultDepth 24
	Subsection "Display"
		Viewport 0 0
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	Screen		0 "Screen0" RightOf "Screen1"
	Screen		1 "Screen1" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "on"
	Option "Clone" "off"
EndSection

---

### Post by mlomker on 2005-10-07
> Will upgrade drivers when i get some time!


You are using the ATI drivers, which I've been told are faster in 2D applications than the fglrx drivers...but there's no comparison in 3D performance.  If you play any games at all then you'll want to change your drivers.

---

### Post by JakeSpeare on 2005-10-07
I play zero games in linux.  So maybe I will just leave it.

Thanks for all your help, once again!

This is a GREAT forum with GREAT people!!

---

### Post by andguent on 2005-10-11
I would like to confirm that this setup worked for my Radeon 7000 VE (RV100 QY) with Ubuntu Breezy RC.

Thanks so much for your work. You made my evening a game of copy paste while watching TV.

As I was writing this, the PC froze. I'm going to blame it on the fact I left the live cd running a couple days to try out Breezy, and no swap space.


"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)" 
dual head dualhead dual monitor dualmonitor

---

