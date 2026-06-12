---
title: "Screen Resolution"
date: 2007-04-22
forum: General Help
---

### Post by meney on 2007-04-22
Hey everyone!

I just bought myself a new 20.1" widescreen monitor, the problem I am having is the ability to set the correct resolution in Ubuntu. I'm currently running Feisty on an Acer Aspire 1694. ATI Mobility Radeon X700. When I flip to the Screen resolution menu in preferences, the highest screen resolution I receive is 1280x800. The screen resolution required for my new monitor is 1680x1050. Does anybody know how may be able to solve my dilemma? 

Thanks!

---

### Post by Dave54 on 2007-04-22
Enter the following into terminal:
```
gedit /etc/X11/xorg.conf
```
In the window that pops up, scroll down to where it says 
```
Section "Screen"
```
(Which is probably at the bottom), and paste that whole section here.

The problem can probably be easily fixed.

---

### Post by meney on 2007-04-22
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection
```

There it is :D

---

### Post by meney on 2007-04-22
PS: The monitor I'm connecting is an LG flatron wide.

---

### Post by Dave54 on 2007-04-23
Great. Now you said that the highest resolution was 1280x800, right? If you look in what you posted, that's all that's listed. So, you just have to add the resolution you want (but make sure your monitor can handle it first).

To open your xorg so you can edit it, use
```
sudo gedit /etc/X11/xorg.conf
```

Now add "1680x1050" in front of each entry of "1280x800" with a space between them.

Just to make sure there's no mistakes, I've done just that:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050" "1280x800"
	EndSubSection
EndSection
```

Oh, and one more thing. Before editing your xorg you should always back it up. I'd use:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.4-23-07
```
This will make a copy xorg.conf called xorg.conf.backup.4-23-07. If something goes wrong, you can run the following to copy the backup back over:
```
sudo cp /etc/X11/xorg.conf.backup.4-23-07 /etc/X11/xorg.conf
```

So, when you do finish editing you xorg, just save and reboot. If you don't want to reboot, you and log out and hit ctrl+alt+backspace. This almost always works.

Tell me if you get the new resolution

edit - by the way, I'm heading to bed so I won't be able to help for a little while :p

---

### Post by meney on 2007-04-23
Yep!!! Works great :D

---

### Post by SaltyTaro on 2007-04-23
How come this doesn't work for me

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection
```
When I go system->preferences->screen resolution, it doesn't have 1280x1024, but has the two lower resolutions which I've deleted.  What have I done wrong

---

### Post by paulmcginniss20 on 2007-04-23
Yeah I have the same problem on my Samsung X50 Laptop. My xorg.conf file is read only, so how can I save the changes I try to make?

---

### Post by dcstar on 2007-04-23
> **paulmcginniss20 said:**
> Yeah I have the same problem on my Samsung X50 Laptop. My xorg.conf file is read only, so how can I save the changes I try to make?

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by paulmcginniss20 on 2007-04-23
^^ Thanks mate, It worked like a charm :)

---

### Post by Dave54 on 2007-04-23
> **SaltyTaro said:**
> How come this doesn't work for me

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection
```
When I go system->preferences->screen resolution, it doesn't have 1280x1024, but has the two lower resolutions which I've deleted.  What have I done wrong

Try adding
```
    Option         "UseEdid" "false"
```
just above the display subsection.

---

### Post by thopar on 2007-04-25
This worked for me.... Thank God!!! I have a Nvidia FX 5200.

Just add         [COLOR="Red"]Option         "UseEdid" "false"[/COLOR]    above display subsection...


TP

---

### Post by SXR on 2007-04-25
I have Ubuntu Running on a PPC g3 B&W series with the ATI rage 128 graphics card Stock on most mac of its type. My monitor how ever is a Sony Diamondtron monster  22' viewable. minimum resolution recommended for the monitor is 1280X1024 I can only get it to go up to 1024x768. How do I add better res to it ?

---

### Post by Dave54 on 2007-04-25
> **SXR said:**
> I have Ubuntu Running on a PPC g3 B&W series with the ATI rage 128 graphics card Stock on most mac of its type. My monitor how ever is a Sony Diamondtron monster  22' viewable. minimum resolution recommended for the monitor is 1280X1024 I can only get it to go up to 1024x768. How do I add better res to it ?

Have you read the beginning of this thread? Here's the solution: [http://ubuntuforums.org/showthread.php?p=2513288#post2513288]("http://ubuntuforums.org/showthread.php?p=2513288#post2513288")

If you still can't get it to work, then edit your xorg, scroll down to where it says 
```
Section "Screen"
```
and paste that whole section here.

---

### Post by saj0916 on 2007-04-25
I have my 20" dell fp2001 set up to view at 1600x1200 and it won't scale down to size. My desktop extends past the monitor and I can scroll right and down to see the extended portions. Does anyone have any clue why this may be happening? Here is my portion of xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" 
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" 
    EndSubSection
EndSection
```

---

### Post by Dave54 on 2007-04-25
> **saj0916 said:**
> I have my 20" dell fp2001 set up to view at 1600x1200 and it won't scale down to size. My desktop extends past the monitor and I can scroll right and down to see the extended portions. Does anyone have any clue why this may be happening?
This might work. First, what resolution are you trying to use? If it's 1600x1200, then try adding the following under "modes" in the 24 bit depth:
```
Virtual 1600 1200
```
If you don't want to use a resolution as high as 1600x1200, then you could delete that entry from the list of modes.

---

### Post by saj0916 on 2007-04-25
Thanks for reply dave. Yes, I am trying to display in 1600x12000, because that is how I currently am set up with XP. I tried to add the Virtual command with no success. In 1280x800 it looks fine on my laptop, but has about 2 inches cut of on my monitor. I have been trying to a dual head set up working, but I do have beryl set up properly. I am pretty sure my drivers for my card are correct but I am pretty stumped on this one since I'm a noob. Here is my entire xorg.conf below. I appreciate the help.


```

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
	Load	"dbe"
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
        Identifier        "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
	Option "MergedFB" "true" #Enable MergedFB function
	Option "MonitorLayout" "LCD, CRT" 
	Option "CRT2Hsync" "31-80" 
	Option "CRT2VRefresh" "56-76" 
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "RightOf" 
	Option "MetaModes" "1600x1200-1600x1200" 
	Option "MergedXineramaCRT2IsScreen0" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-81
	VertRefresh	60
	# V-freq: 80.00 Hz  // h-freq: 100.84 KHz
 	Modeline "1600x1200" 271.06  1600 1736 2064 2688  1200 1200 1204 1260 

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
	Virtual 1600 1200
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
	Virtual 1600 1200
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
	Virtual 1600 1200
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" 
	Virtual 1600 1200
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
	Virtual 1600 1200
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768"
	Virtual 1600 1200
    EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier        "Default Layout"
        Screen                "Default Screen"
        InputDevice        "Generic Keyboard"
        InputDevice        "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice        "Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by strabes on 2007-04-25
It's probably because the monitor's max resolution is smaller than 1600x1200.

---

### Post by saj0916 on 2007-04-25
[http://docs.us.dell.com/support/edocs/monitors/2001fp/en/specs.htm#resolution](http://docs.us.dell.com/support/edocs/monitors/2001fp/en/specs.htm#resolution)

According to dell's manual on it the optimal resolution is 1600 x 1200.

---

### Post by Dave54 on 2007-04-25
> **saj0916 said:**
> [http://docs.us.dell.com/support/edocs/monitors/2001fp/en/specs.htm#resolution](http://docs.us.dell.com/support/edocs/monitors/2001fp/en/specs.htm#resolution)

According to dell's manual on it the optimal resolution is 1600 x 1200.

Posting your xorg and documentation really helped. I've pulled as many tricks as I could and fixed up your monitor and screen sections:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-76
        Modeline        "1600x1200_60"   162   1600 1664 1856 2160   1200 1201 1204 1250  +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
        Option          "UseEdid" "false"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200_60" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200_60" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200_60" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200_60" "1280x1024" "1152x864" "1024x768" 
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200_60" "1280x1024" "1152x864" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200_60" "1280x1024" "1152x864" "1024x768"
    EndSubSection
EndSection
```

Be sure to back up your xorg first!
Replace the monitor and screen sections with what I have here, save, reboot, etc.
If this doesn't work, I'll be disappointed, but I think I'll have another Idea.

Good luck

Edit: If it doesn't work, try changing your screen resolution to a smaller option, then back to 1600x1200. Also, check for multiple refresh rates under 1600x1200, and try each.

Edit again
> I have been trying to [get] a dual head set up working
I'm not sure what you mean here, but are you using two monitors?
Is one an LCD and the other CRT?
The usual reason you get a virtual desktop the wrong size is that you requested a resolution that could not be calculated or rendered. If you have two monitors, I don't know how you'd specify what monitor is capable of what. Possibly two "screen" and "monitor" sections?

---

### Post by saj0916 on 2007-04-25
I appreciate all the help dave, and in regards to the monitors I have a Dell Inspirion 9100 laptop with a 20" + 17" LCD hooked up to my dual output card. Thanks for putting the time in and editing my xorg.conf; I will be testing it out very shortly.

---

