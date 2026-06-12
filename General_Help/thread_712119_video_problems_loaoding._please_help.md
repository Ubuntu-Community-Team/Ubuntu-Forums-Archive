---
title: "video problems loaoding. please help"
date: 2008-03-01
forum: General Help
---

### Post by RiPPeR777 on 2008-03-01
ok. i have been trying alot of different options in trying to get ubuntu to work and im just about to give up. First of all when i used the live CD install "7.10" after the boot splash screen my monitor just went blank and nothing was happening. so i read some things and was informed that using the Alt cd with text mode install would work. and it did i now have ubuntu 7.10 installed on my computer, but with the same problems. after the boot splash screen my monitor just goes black again. so i read some more one these forms and in the irc chat. i installed new drivers via "sudo apt-get install nvidia-glx-new" then eidited my xorg.conf files and changed driver used from "nv" to "nvidia" after i did all this the problem actually got worse. now instead of the screen going blank after the boot splash screen my monitor losses its signal to my comp. how lovely!!! so now i cant get into terminal with out loading in recovery mode. so i though to myself hey well that made things worse so. i went back to xorg.conf and changed "nvidia" back to "nv". when i did that it still has the same problem as before that my monitor just goes black. but i can still access terminal via "ctrl+alt+F1" and login and everything just cant run x still.  below is my xorg.cong file.

Section "Files"
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
	Identifier	"nVidia Corporation G70 [GeForce 7800 GT]"
	Driver		"nvidia"
	BusID		"PCI:4:0:0"
EndSection

Section "Monitor"
	Identifier	"VA912-4SERIE"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7800 GT]"
	Monitor		"VA912-4SERIE"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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
EndSection

---

### Post by Pelham123 on 2008-03-01
Get a terminal up and running and reconfigure X: Back up your existing xorg.conf file first (I know it doesn't work well, but...)

Sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by WestCoastSuccess on 2008-03-01
I used to have the same problem you're having (when you tried the nvidia drivers - ie monitor wouldn't respond and I'd get "signal out of range" message). As a workaround, I'd simply hit Ctrl+Alt+Backspace and it would go to the X login screen. Go back to that configuration and see if that works to get you going for now, anyway.

I think the problem disappeared when I upgraded from Feisty to Gutsy - it just works now, and it's been long enough now that I can't recall if I had to tinker with anything else - sorry!

By the way, what's the native resolution of the screen you're using?

Cheers!

---

### Post by RiPPeR777 on 2008-03-01
thanx ill try restarting x by hitting ctrl+alt+backspace" but i dont see how that will restart my connect with my monitor.

another thing is cant i just edit my xorg.conf with the nano cmd???

---

### Post by RiPPeR777 on 2008-03-01
ok i have loaded my xorg.0.log here  [http://paste.ubuntu-nl.org/57989/](http://paste.ubuntu-nl.org/57989/)  please take a look.

---

### Post by RiPPeR777 on 2008-03-01
i think i figured it out finnaly

---

### Post by WestCoastSuccess on 2008-03-02
For starters it looks to me like the BusID in the Device section is incorrect - you don't need that setting - ubuntu will figure it out.

Also, I'd get rid of the complicated identifiers and use "Monitor0" "Videocard0" and "Screen0".

Do you have a Module section? Mine reads:

Section "Module"
    Load           "dbe"
    Load          "fbdevhw"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load          "record"
EndSection

Anyway, it seems you've made some progress - what did you do?

---

### Post by WestCoastSuccess on 2008-03-11
Would you mind posting your solution for others who may encounter the same issue?

Cheers!

WCS

---

