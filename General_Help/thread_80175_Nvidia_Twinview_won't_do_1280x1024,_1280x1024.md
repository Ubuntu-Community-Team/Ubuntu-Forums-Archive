---
title: "Nvidia Twinview won't do 1280x1024, 1280x1024"
date: 2005-10-21
forum: General Help
---

### Post by brownjor on 2005-10-21
Hi all,

I am having a problem getting Nvidia twinview to work on my computer.  I have two nearly identical LCD 19" screens hooked up to a GForce 4 MX 440 with 2 VGA outs.

I've downloaded and installed the nvidia drivers.  I can get the twinview to work with 1024x768, 1024x768, but when I set it any higher I get an error and X won't start.  It says something like, no screens available.  

Right now I have it set up so that each monitor displays a seperate X desktop at 1240x1024, but this setup is less then desirable, since I cannot drag windows between the two, and various other problems.  (seperate profiles for apps, etc)

I've included my xorg.conf file below.  With the below file, my desktop loads up with the monitors in 1024x768.  This is also not good since the monitors were designed for 1240x1040, and don't look as nice.  

Can anyone see anything that I need to do to get this to work?

Thanks!
-Jordan

[HTML]
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
#	Load	"glx"
	Load	"int10"
	Load	"type1"
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
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "TwinView"      "true"
        Option          "RenderAccel"   "true"
        Option          "UseEdidFreqs"  "true"
        Option          "SecondMonitorHorizSync"     "30-69"
        Option          "SecondMonitorVertRefresh"   "50-75"
        Option          "MetaModes"                  "1280x1024, 1280x1024 ; 1024x768,1024x768"
        Option          "TwinViewOrientation"        "LeftOf"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
EndSection[/HTML]

---

### Post by jonesy on 2005-10-21
Ok, a few things:

You don't need to disable GLcore and glx.  Just the Load "dri" should be commented out. A couple other things you can try are including a separate monitor identifier for your second montior.  Both monitors I believe need to be included in the "Screen" definition.  See the excerpt from my working configuration below:

[HTML]
Section "Monitor"
        Identifier      "G90fb-2"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier   "SyncMaster955DF"
        VendorName   "Samsung"
        ModelName    "SyncMaster 19 inch"
#        HorizSync    30.0 - 95.0
#        VertRefresh  50.0 - 160.0
        Option      "dpms"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Monitor         "G90fb-2"
        DefaultDepth    16
        Option      "TwinView" "true"
        #Option      "IgnoreEDID" "true"
        #Option      "SecondMonitorHorizSync" "30.0 - 95.0"
        #Option      "SecondMonitorVertRefresh" "50.0 - 160.0"
        Option      "MetaModes" "1600x1200,1600x1200; 1280x1024,1280x1024"
        Option      "TwinVeiwOrientation" "LeftOf"
        Option      "ConnectedMonitor" "G90fb-2, SyncMaster955DF"
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
[/HTML]

---

### Post by jonesy on 2005-10-21
I just noticed that all of my TWINVIEW options are also under the Screen section instead of the Device section, don't know if that makes a difference, never tried it the other way.  Hope this helps.

---

