---
title: "urgent help needed Unable to set monitor resolution and refresh rate."
date: 2007-06-30
forum: General Help
---

### Post by umairsaeed219 on 2007-06-30
i want to set my monitor resolution and refresh rate on **7.04** in this regard i have tried to search already posted threads but now in the end i am helpless i dont know what to do 
Now i want you people to help me 

Following are the specification of my monitor

> [B]philips monitor model # 
105S7[/B]
    * 15-inch (13.8" VIS) color monitor with excellent front of screen performance for use with MACs and PCs
    * Autoscan covers horizontal frequencies up to 54 kHz offering a maximum resolution of 1024 x 768 with flicker free display of 800 x 600 at up to 85 Hz
    * Flat square High Contrast CRT with high-resolution 0.28 mm dot pitch .

**Technical Specifications***

CRT
• Size and deflection 	15 inch / 38 cm ; 90° deflection angle
• Dot pitch 	0.28 mm• Tube type 	Shadow mask, flat square, high contrast• Phosphor 	P22
• Recommended display area 	10.6" x 8.0" / 270 x 202 mm
• Maximum display area 	11.1" x 8.4" / 284 x 214 mm
  	
SCANNING
[B]• Horizontal scanning 	30 - 54 KHz
• Vertical scanning 	50 - 120 Hz[/B]
  	 
VIDEO
• Video dot rate 	85 MHz
• Input impedance 	
- Video 	75 ohm
- Sync 	1k ohm
• Input signal levels 	0.7 Vpp
• Sync input signal
	TTL Sync
• Sync polarities 	Positive and negative
  	 
WHITE COLOR TEMPERATURE
Chromaticity CIE coordinates:
• at 9300   K 	x = 0.283 / y = 0.297
• at 6500   K 	x = 0.313 / y = 0.329
• at 5500   K 	x = 0.332 / y = 0.347
  	 
**PRESET MODES**

720 x 400 @ 70 Hz
640 x 480 @ 60 Hz
640 x 480 @ 75 Hz
800 x 600 @ 75 Hz
800 x 600 @ 85 Hz
1024 x 768 @ 60 Hz
	 
following are results of  lspci
> umair@umair-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

Now here are the steps which i have already followed but failed(i have followed the command 
sudo dpkg-reconfigure xserver-xorg when i was using 6.06lts and it has worked for me but now it is not working on 7.04)

first of all i have tried the same command to reconfigure(not make back up copy because i dont know how to back up and later use it) the command is
 
> sudo dpkg-reconfigure xserver-xorg
after that i select **vesa**
afer that there were no of option which i dont know so leave them on default

when comes the monitor detection portion automatic detection produced following result
> &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474; The X server configuration file associates the monitor with a name    
  &#9474; that you may provide.  This is usually the vendor or brand name        
  &#9474; followed by the model name, e.g., "Sony E200" or "Dell E770s".       
  &#9474;                                                                      
  &#9474; Identifier for the monitor:                           
  &#9474; Generic Monitor_____________________________________________________  
  &#9474;                                                                    <Ok>  

after that video modes to be used by x server i didnot choose any thing and leave them as default
after that i choose 
> Method for selecting the monitor characteristics:          
                                                                       
                         Simple                                 
                         Medium                             
                         Advanced                               
                                                                  
                                  <Ok>            
**advance and right horizontal scanning 30-54khz and vertical 50-120hz      **   
after that i write thes changes by pressing yes
in next step it asked me 
> Usually 24-bit color is desirable, but on graphics cards with        
limited amounts of framebuffer memory, higher resolutions may be       
achieved at the expense of higher color depth.  Also, some cards      
support hardware 3D acceleration only for certain depths.  Consult    
your video card manual for more information.                          
So-called "32-bit color" is actually 24 bits of color information     
plus 8 bits of alpha channel or simple zero padding; the X Window      
System can handle both.  If you want either, select 24 bits.
i select 24 bits and restart my x but nothing came up an error message appears which says your x server wrongly configured no gui displayed itried to reconfigureit using recovery mood but all in vane i never get back my gui login screen 
then i again tried to reconfigure and in this time i select 16 bits instead of 24 bits this atleast give me my GUI but with following resolution 640*680 and 86hz
plz help me to identify where i am wrong 

remember i have also tried following commands
> sudo dpkg-reconfigure -phigh xserver-xorg

before reconfiguring my x server i was using 1024 x 768 @ 60 Hz i just want to upgrade my refresgh rate to 85 which was only possible at 800x600 (as on my windows xp)
so please restore my previous or set mydesired resolution and refresh rate 800x600 and 85hz

---

### Post by Sepero on 2007-07-07
I arrived at your post because you apparently have a dialup modem, Intel 536ep. I wanted to drop you a link to where you can download a prepackaged driver for Feisty 7.04.
[http://ubuntuforums.org/showthread.php?p=2930571](http://ubuntuforums.org/showthread.php?p=2930571)


As for your monitor problems, here's a copy of my /etc/X11/xorg.conf file. Hopefully it can help you out:
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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

Section "Monitor"
	Identifier	"E70-5"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"E70-5"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mactece on 2007-07-08
I don't understand a word of the posts above and I apologise if this is no help at all but...

I lost the resolution for my monitor and couldn't see a thing. So I reinstalled the graphics card and when it was redetected the settings came back.

---

