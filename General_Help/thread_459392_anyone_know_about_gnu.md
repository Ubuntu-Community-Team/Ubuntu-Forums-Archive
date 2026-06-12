---
title: "anyone know about gnu??"
date: 2007-05-30
forum: General Help
---

### Post by letitworknow on 2007-05-30
my ubuntu 7.04 freezes at the log in .   i foung a fix on a google serch but i need to get into gnu nano.  i did this from  a rcovery boot.  from there i need to get to         section "device"      
ther are otpions at the bottom of the screen for example  ^page up          but i dont know how to access this.    please help.  if this works i will post the whole fix cause it seems like a fairly common problem
thank you

---

### Post by Swab on 2007-05-30
You can use the up and down arrows on your keyboard to scroll through the file you are editing.  When finished you can press Ctrl + o to save the changes you made.

---

### Post by letitworknow on 2007-05-30
that didnt work the arrows only move the cursur down two lines. i can hold shift and push page up to bring me throw the boot prossess   look at this and let me know if it makes sense

1. Boot into recovery mode. It will get you to a command line.

2. Type: sudo nano /etc/X11/xorg.conf

3. Find the section titled: Section "Device"

4. As the last entry under "Device" add the line: Option "NoAccel"

5. Ctrl-O to save

6. Ctrl-X to exit

7. Reboot in normal mode

8. Rejoice that your mouse will work and Gnome will load and that once again, everything is good in the world!

---

### Post by Swab on 2007-05-30
Are you sure you are opening the correct file with Nano?  Remember paths and filenames are case sensitive in Linux.  So X11 is not the same as x11.   Once the correct file is open then the arrow keys will allow you to scroll.

---

### Post by letitworknow on 2007-05-30
thanks for the help.  it was a caps issue.  but it didnt work now after the ubuntu prpgress bar comes up i get a sreen that says my x server is not set up right  ooooo well

---

### Post by Swab on 2007-05-30
Perhaps if you could post the contents of your /etc/X11/xorg.conf file someone might be able to help.

---

### Post by letitworknow on 2007-05-30
well here it is. yes i typed it all out. i double checked as i went so i hope it is all right





Section “Files”
	FontPath 	“/usr/share/fonts/X11/misc”
	FontPath 	“/usr/share/fonts/X11/cyrillic”
	FontPath 	“/usr/share/fonts/X11/100dpi/:unscaled”
	FontPath 	“/usr/share/fonts/X11/75dpi/:unscaled”
	FontPath 	“/usr/share/fonts/X11/Type1”
	FontPath 	“/usr/share/fonts/X11/100dpi”
FontPath 	“/usr/share/fonts/X11/75dpi”
# path to defoma fonts
FontPath	“/var/lib/defoma/x-ttcidfont-conf.d/dirs.TrueType”
EndSection

Section “Module”
	Load	“i2c”
	Load	“bitmap”
	Load	“ddc”
	Load	“dri”
	Load	“extmod”
	Load	“freetype”
	Load	“glx”
	Load	“int10”
	Load	“vbe”
EndSection

Section “inputDevice”
	Identifier	“Deneric Keyboard”
	Driver		“dbd”
	Option		“CoreKeyboard”
	Option		“XkbRules”	“xorg”
	Option		“XkbRules”	“pc105
Option		“XkbRules”	“us”
EndSection

Section “inputDevice”
	Identifier	“Confugured Mouse”
	Driver		“mouse”
	Option		“CorePointer”
	Option		“Device”		“/dev/input/mice”
Option		“Protocol”		 “ImPS/2”
Option		“ZaxisMapping”	“4  5”
Option		“Emulate3Buttons”	“true”
EndSection

Section “inputDevice”
	Driver		“wacom”
	Identifier	“stylus”
	Option		“Device”	“/dev/input/Wacom”
	Option		“Type”		“stylus”
	Option		“ForceDevice”		“ISDV4”	#    Tablet PC ONLY
EndSection

Section “inputDevice”
	Driver		“wacom”
	Identifier	“stylus”
	Option		“Device”	“/dev/input/Wacom”
	Option		“Type”		“stylus”
	Option		“ForceDevice”		“ISDV4”	#    Tablet PC ONLY
EndSection

Section “inputDevice”
	Driver		“wacom”
	Identifier	“stylus”
	Option		“Device”	“/dev/input/Wacom”
	Option		“Type”		“stylus”
	Option		“ForceDevice”		“ISDV4”	#    Tablet PC ONLY
EndSection

Section “Device”
	Identifier	“Intel Corporation 82G965 Integrated Graphics Controlle$
	Driver		“i810”
	BusID		“PCI:0:2:0”
Option “NoAccel”
EndSection

Section “Monitor”
	Identifier	“LT716s”
	Option		“DPMS”
EndSection

Section  “Screen”
	Identifier	“Default Screen”
	Device		“Intel Corporation 82G965 integrated Graphics Controlle$
	Monitor	LT716s”
DefaultDepth	24
SubSection “Display”
	Depth		1
	Modes		“1280x1024”  “1024x768”  “832x624”   “800x600”  “720$
    EndSubSection
SubSection “Display”
	Depth		1
	Modes		“1280x1024”  “1024x768”  “832x624”   “800x600”  “720$
    EndSubSection
SubSection “Display”
	Depth		1
	Modes		“1280x1024”  “1024x768”  “832x624”   “800x600”  “720$
     EndSubSection
SubSection “Display”
	Depth		1
	Modes		“1280x1024”  “1024x768”  “832x624”   “800x600”  “720$
     EndSubSection
SubSection “Display”
	Depth		1
	Modes		“1280x1024”  “1024x768”  “832x624”   “800x600”  “720$
    EndSubSection
SubSection “Display”
	Depth		1
	Modes		“1280x1024”  “1024x768”  “832x624”   “800x600”  “720$
    EndSubSection
EndSection

Section “ServerLayout”
	Identifier	“Default Layout”
	Screen		“Default Screen”
	InputDevice	“Generic Keyboard”
	InputDevice	“Configured Mouse”
	InputDevice	“stylus”	“SendCoreEvents”
	InputDevice	“Cursor”	“SendCoreEvents”
EndSection

Section “DRI”
	Mode 0666
EndSection

---

### Post by letitworknow on 2007-05-31
anybody have any ideas??

---

### Post by Swab on 2007-06-01
I don't know what is wrong with it.  You could try to reconfigure X with the following.

sudo dpkg-reconfigure xserver-xorg

---

### Post by eyelessfade on 2007-06-01
the content of /var/log/Xorg.0.log might tell us what is wrong :)

---

