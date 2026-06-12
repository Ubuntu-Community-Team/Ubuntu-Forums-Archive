---
title: "Compiz Desktop Effects Nightmares"
date: 2008-06-05
forum: General Help
---

### Post by glich509 on 2008-06-05
After Hours upon Hours of editing my xorg.conf file and downloading package after package I still cannot get any desktop effects to work.  I had the whole compiz package with all the effects working perfectly on 7.10 but then as soon as I upgraded to 8.04 nothing has been working.  The following are the results from compiz-check and from the compiz command as well as my xorg.conf file.  Any help would be greatly appreciated. (I have an ATI Mobility radeon 7500)
```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

```
glich509@GDL:~$ compiz
Checking for Xgl: not present. 
Found laptop using radeon driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

```
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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

Section "Module"
        Load            "glx"
        Load            "dri"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname       "ATI Radeon"
	BusID		"PCI:1:0:0"
        Driver		"radeon"
        Screen          0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
        Option          "AccelMethod" "XAA"
        Option          "EXANoComposite" "false"
        Option          "FBTexPercent" "50"
        Option          "MigrationHeuristic" "greedy"
        Option          "DRI" "true"
        Option          "GARTSize"     "1024"
        Option          "AGPMode" "1"
        Option          "AGPFastWrite" "1"
        Option          "ColorTiling" "1"
        Option          "XAANoOffscreenPixmaps" "true"
        Option          "EnablePageFlip" "1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
                Depth           24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice	"Synaptics Touchpad"
        Option          "AIGLX" "True"
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
        Option          "Composite" "Enable"
EndSection

Section "DRI"
        Group           "video"
        Mode            0660
EndSection
```

Any Suggestions?

---

### Post by qamelian on 2008-06-05
The problem is not in your xorg.conf. Many ATI cards have  been blacklisted as they have had issues with compiz. YOu can try to correct the problem by doing the following:

1) Go to Applications > Accessories > Terminal.
2) In the terminal window, type:
```
gksu nano /usr/bin/compiz
```
3) On a ne line after the initial block of comments (Lines starting with #), insert the following line:
```
SKIP_CHECKS="yes"
```
4) Press Ctrl-O to save the file.
5) Press Ctrl-X to exit nano.

You should now be able to activate the desktop effects.

---

### Post by glich509 on 2008-06-05
I added the line to the compiz file and still no luck.

---

### Post by qamelian on 2008-06-05
> **glich509 said:**
> I added the line to the compiz file and still no luck.
This may be because of the editing you've done on your xorg.conf. Did you keep a backup of the original xorg.conf from before you started editing? If so, you may need to restore the original file. There should be no need at all to edit xorg.conf to get compiz working on this card.

If you have no back up copy, you can drop to the terminal again and type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You will be prompted for a couple of pieces of information. This command will create a fresh, correct xorg.conf for you, after which you should close all apps and press Ctrl-Alt-Backspace to restart your xserver for the changes to take effect.

---

### Post by glich509 on 2008-06-05
I replaced the changed xorg.conf with the original and just like that it all works again.  Its amazing how simple the solution actually was and all the unecessary steps I took to try and fix it.  Thanks so much for all your help!!

---

### Post by qamelian on 2008-06-05
> **glich509 said:**
> I replaced the changed xorg.conf with the original and just like that it all works again.  Its amazing how simple the solution actually was and all the unecessary steps I took to try and fix it.  Thanks so much for all your help!!
No problem. I had the same problem on my laptop. Just so you know: if an update to compiz gets installed by the updater, it is extremely like to break again as /usr/bin/compiz may get over-written with a newer version. Just add the line from my first instructions into the new version of /usr/bin/compiz and everything should work fine again.

:)

---

