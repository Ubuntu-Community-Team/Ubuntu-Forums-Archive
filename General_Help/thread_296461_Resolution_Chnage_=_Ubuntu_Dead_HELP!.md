---
title: "Resolution Chnage = Ubuntu Dead HELP!"
date: 2006-11-09
forum: General Help
---

### Post by olieviya on 2006-11-09
I have tried the way suggested to others to change my resolution on linux but I ruined my ubuntu installation. I was forced to install it all over again not that it was hard or took time like some other os installations ;)

What I really want is to be able to change to 1280 * 800 because my screen looks very crappy with 1024*768 esp since it's widescreen and everything looks squashed/stretched. I have no clue how to make ubuntu work with the 1280*800 resolution. I HAVE tried what was suggested in other similar threads all I got when I restarted my laptop was: blank black screen & laptop non-responsive. 


Please help!!! :(
(I'm a newbie to linux even though I have been using it on-and-off for that last year or so. Experienced windows user so don't expect a lot of command line knowledge from me.)
:-?

---

### Post by olieviya on 2006-11-09
Just like to mention that my graphics card is ATI and it seems to be having trouble with the refresh rate as well.

---

### Post by SRParda on 2006-11-09
The route for a generic solution (instead of a try and error method) is in:
[http://xorg.freedesktop.org/wiki/FAQVideoModes](http://xorg.freedesktop.org/wiki/FAQVideoModes)
In that page explains how to obtain additional video modes supported by your monitor, reading the X log.

So you can construct the exact modeline for your monitor.


Here is an example for 1280x768, build for 1280x768 with the data contained in the X logs:

In /etc/X11/xorg.conf:
[COLOR="Gray"][SIZE="1"]

Section "Monitor"
Identifier "Videoseven LTV30C"
DisplaySize 643 386
HorizSync 30-64
VertRefresh 56-75
Option "DPMS"
ModeLine "1280x768" 81.00 1280 1344 1472 1664 768 771 778 798
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
Monitor "Videoseven LTV30C"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x768"
EndSubSection
EndSection[/SIZE][/COLOR]

---

### Post by olieviya on 2006-11-09
I am a little confused by your reply, though grateful :)
Am i supposed to manually edit the file?
How do I find the info to replace it with and what sort of stuff am I looking to change?

---

### Post by olieviya on 2006-11-10
> **SRParda said:**
> The route for a generic solution (instead of a try and error method) is in:
[http://xorg.freedesktop.org/wiki/FAQVideoModes](http://xorg.freedesktop.org/wiki/FAQVideoModes)
In that page explains how to obtain additional video modes supported by your monitor, reading the X log.

So you can construct the exact modeline for your monitor.


Here is an example for 1280x768, build for 1280x768 with the data contained in the X logs:

In /etc/X11/xorg.conf:
[COLOR="Gray"][SIZE="1"]

Section "Monitor"
Identifier "Videoseven LTV30C"
DisplaySize 643 386
HorizSync 30-64
VertRefresh 56-75
Option "DPMS"
ModeLine "1280x768" 81.00 1280 1344 1472 1664 768 771 778 798
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
Monitor "Videoseven LTV30C"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x768"
EndSubSection
EndSection[/SIZE][/COLOR]

do i need to install ther ati drivers?

---

### Post by Zeratul7 on 2006-11-10
According to my experience most resolution promblems are caused by these 2 missing parameters from xorg.conf file.

```

HorizSync 30-64
VertRefresh 56-75

```

Just replace these numbers with your monitor specific parameters. If You cannot find it from Your display user-manual then You may try find the parameters with google. That's how I enabled all possible resolutions for my laptop.

---

### Post by SRParda on 2006-11-11
> **olieviya said:**
> do i need to install ther ati drivers?

The ATI driver is supposed to be installed, and your problem is the screen configuration.

Yo can see what ati driver you have installed reading the xorg.conf file, but in other section:

For ATI propietary drivers that section will look like:
[SIZE="1"][COLOR="Gray"]Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection[/COLOR][/SIZE]

But this is not, probably, your problem,  .

---

### Post by SRParda on 2006-11-11
> **olieviya said:**
> I am a little confused by your reply, though grateful :)
Am i supposed to manually edit the file?
How do I find the info to replace it with and what sort of stuff am I looking to change?

Yes, you have to edit the xorg.conf file (with administrative rights)

To edit it, you can type at $ prompt in a terminal window:
[COLOR="Teal"][INDENT]sudo gedit /etc/X11/xorg.conf[/INDENT][/COLOR]
What you have to write , require you to read the info write in the X's log file. To read the log you can type at prompt:
[COLOR="Teal"][INDENT]sudo gedit /var/log/Xorg.0.log[/INDENT][/COLOR]
There you can find a section "additional video modes", detalling resolutions not available by default. It would had data for 1280x800.
As explained at: [http://xorg.freedesktopa.org/wiki/FAQVideoModes](http://xorg.freedesktopa.org/wiki/FAQVideoModes), you can read the values valids to manually define the video mode.

You will have to add the red lines (with yor specific values!) or change them if they are already defined.
All the data to write in that line, would be obtained reading the (big) Xorg.0.log file.
You define the video mode writing a modeline line in the Monitor section:

[COLOR="Gray"][SIZE="1"]Section "Monitor"
[INDENT]Identifier "Videoseven LTV30C"
[COLOR="Sienna"]DisplaySize 643 386
HorizSync 30-64
VertRefresh 56-75[/COLOR]
Option "DPMS"
[COLOR="Sienna"]ModeLine **"1280x768"** 81.00 1280 1344 1472 1664 768 771 778 798[/COLOR]
[/INDENT]EndSection[/SIZE][/COLOR]

At that moment you will have defined a video mode for your monitor. (Note we have named it **[COLOR="Sienna"]"1280x768"[/COLOR]** in that line, in your case it will be 1280x800 and the data for that mode instead of my data). 

Now you have to make it available for the screens xorg draw and send to monitor, that is acompplised adding the mode to the screens resolutions for any bit depth. In the example:

[COLOR="Gray"][SIZE="1"]Section "Screen"
[INDENT]Identifier "Default Screen"
Device "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
Monitor "Videoseven LTV30C"
DefaultDepth 24

   SubSection "Display"
[INDENT]      Depth 24
      Modes [COLOR="Sienna"]"1280x768"[/COLOR] "1024x768"[/INDENT]
   EndSubSection
[/INDENT]
EndSection[/SIZE][/COLOR]

Note: I only copied the subsection for the default 24 bit color depth. 
You are required to add "1280x800" in the modes line (in your case), that is: the same name that we defined in the above section for monitor.
Usually you will have more section display to fill, for each bit depth defined.

Once you have read Xorg.0.log, you can post the additional video modes to help you to obtain video mode data for modeline.

---

### Post by olieviya on 2006-11-11
II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 813 v_border: 0
(II) VESA(0):  CPT



Thanks a lot, hope this works, I have just wqrote the changes to the xorg and will restart x now.

---

### Post by olieviya on 2006-11-11
:( I have ruined Ubuntu again, I can only access it via a command prompt only boot up. Any ideas?

:(

---

### Post by CatKiller on 2006-11-11
> **olieviya said:**
> :( I have ruined Ubuntu again, I can only access it via a command prompt only boot up. Any ideas?

If you made a backup of your xorg.conf before you changed it, you can use the command line to copy it back.

```
sudo cp /etc/X11/xorg.conf.whatever.you.called.your.backup /etc/X11/xorg.conf
``` **Ctrl-Alt-Backspace** should restart your X server once you've done this.

---

### Post by olieviya on 2006-11-11
I have stupidly forgotten what I called it. I suppose i can locate it if i try.

Still, I need to fix this screen, anybody have any ideas or am I just doing what you guys are suggesting wrongly?

---

### Post by CatKiller on 2006-11-11
> **olieviya said:**
> I have stupidly forgotten what I called it. I suppose i can locate it if i try.

If you press Tab when you've typed in some of the path, it will complete as much of the rest as it can. Pressing Tab again will give you a list of files that match what you've typed to far. You could use this to find out what you save it as. Or you could use ```
sudo ls /etc/X11/
``` to show you a list of the files that are in that directory. Also, if you used GEdit to change the file, it may have automatically made a backup of the last file before you saved as xorg.conf~.

> Still, I need to fix this screen, anybody have any ideas or am I just doing what you guys are suggesting wrongly?

Maybe. That modeline stuff is way over my head. It would probably work, though. I've always (for, like, 3 monitors - hardly a representative sample) used the method of specifying the HorizSync and VertRefresh values. I take it you've actually got the mode you want listed in the Screen section of your xorg.conf?

---

### Post by jimbob on 2006-11-11
There is a nifty modeline generator in Edgy (and maybe some other releases too) named gtf.

To calculate the mode line for 1280x800 at 60HZ for example enter on the command line:  #gtf 1280 800 60 
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by SRParda on 2006-11-11
> **olieviya said:**
> II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 813 v_border: 0
(II) VESA(0):  CPT




You have not post all data for monitor, Min-Max Freq.Horiz. and Min-Max Freq. Vert are needed (data in red)

Section "Monitor"
Identifier "Videoseven LTV30C"
[COLOR="Blue"]DisplaySize 331 207[/COLOR]
[COLOR="DarkRed"]HorizSync xx-xx
VertRefresh xx-xx[/COLOR]
Option "DPMS"
[COLOR="Blue"]ModeLine "1280x800" 68.90 1280 1304 1336 1408 800 801 804 813[/COLOR]
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
Monitor "Videoseven LTV30C"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes [COLOR="Blue"]"1280x800"[/COLOR]
EndSubSection
EndSection

---

### Post by olieviya on 2006-11-12
Yeah, it works 


 gtf 1280 800 60

  # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
  Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

---

### Post by olieviya on 2006-11-12
Is it somewhere in there? :S



(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.12
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: M54P
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: CPT  Model: 13b1  Serial#: 0
(II) VESA(0): Year: 2006  Week: 21
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.615 redY: 0.332   greenX: 0.315 greenY: 0.561
(II) VESA(0): blueX: 0.152 blueY: 0.127   whiteX: 0.315 whiteY: 0.329
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 813 v_border: 0
(II) VESA(0):  CPT
(II) VESA(0):  CLAA154WA05A
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00056a1
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8

---

### Post by olieviya on 2006-11-12
I dunno really, I am a little confused. :)

---

### Post by olieviya on 2006-11-12
Do I now know all the information I need to do it myself??:-?

---

### Post by jordilin on 2006-11-12
I had the same problem as you. Ubuntu installed itself with a predefined resolution and I couldn't change it to 1280x1024. There are two solutions. When installing at boot screen choose your preferred resolution, or once installed go to xorg.conf and in the section screen write down your resolution such as
> Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

It works my friend, I wish you good luck

---

### Post by olieviya on 2006-11-12
> **jordilin said:**
> I had the same problem as you. Ubuntu installed itself with a predefined resolution and I couldn't change it to 1280x1024. There are two solutions. When installing at boot screen choose your preferred resolution, or once installed go to xorg.conf and in the section screen write down your resolution such as

It works my friend, I wish you good luck

I'm sorry, I don't understand.


EDIT: Isn't what you are saying what I have already been told to do and failed?

---

### Post by olieviya on 2006-11-12
I think now that I have pasted all the info maybe somebody can help?:confused:

---

### Post by CatKiller on 2006-11-12
> **olieviya said:**
> I think now that I have pasted all the info maybe somebody can help?:confused:

So what **does** your xorg.conf look like now?

```
cat /etc/X11/xorg.conf > Desktop/xorg.conf.txt
``` will give you a text file on your Desktop you can either copy and paste or attach to a post.

---

### Post by olieviya on 2006-11-12
> **CatKiller said:**
> So what **does** your xorg.conf look like now?

Um, I reverted it back to it's initial state. Look at the next post ;)

---

### Post by olieviya on 2006-11-12
[SIZE="1"][FONT="Courier New"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Option		"XkbLayout"	"gb"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/FONT][/SIZE]

---

### Post by olieviya on 2006-11-12
I'd start messing about but I've already messed up the system 3 times. I have pasted both files needed, but I am at a loss.... anybody can help??](*,)

---

### Post by jimbob on 2006-11-12
Here is a copy of my xorg.conf from my laptop showing how the 1280x800 resoultion should be.   Maybe you can modify mine by just changing the device and monitor sections as needed.

When you select the System->preferences->screen resolution does it show 1280x800 as available?

I take it you have a copy of a working xorg saved so try to generate a new one using #dpkg-reconfigure xserver-xorg taking all the defaults as you go until the resolution comes up then select 1280x800.  If I remember correctly it will give you a chance to try it out before committing.

If 1280x800 does not show up I would suggest that your video card is incapable or something may be wrong with it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by olieviya on 2006-11-12
> **jimbob said:**
> When you select the System->preferences->screen resolution does it show 1280x800 as available?

No, I do not.

> **jimbob said:**
> I take it you have a copy of a working xorg saved so try to generate a new one using #dpkg-reconfigure xserver-xorg taking all the defaults as you go until the resolution comes up then select 1280x800.  If I remember correctly it will give you a chance to try it out before committing.

It doesn't and it also causes the screen to be completely black and non-responsive when I select 1280*800 and restart x.

> **jimbob said:**
> If 1280x800 does not show up I would suggest that your video card is incapable or something may be wrong with it.

But... it's on 1280*800 in winXP... :confused:

---

### Post by Velotix on 2006-11-12
> But... it's on 1280*800 in winXP...

Prove this with a screenshot, please. I ask this because you're not the first person to get the resolution they're after wrong this week. :)

You might actually be after 1280x1024, which is a standard resolution that virtually everything supports these days.

When editting xorg.conf, not only do you need to change the resolution to the one you're after, but you also need to change the vertical refresh and horizontal sync rate, all of which are saved in the xorg.conf file. I've had a long string of problems trying to get my resolution right and I finally have it set up correctly now, so it's mainly trial and error. Don't ever be afraid to mess around with your computer's settings to get it running properly, otherwise it won't ever be how you want it. Just remember to make a backup of any file you're going to change just in case things go wrong (like here).

---

### Post by CatKiller on 2006-11-12
> **olieviya said:**
> Um, I reverted it back to it's initial state. Look at the next post ;)

From the top, then.

The VESA driver will not, as far as I know, do 1280x800. So while you have "vesa" as the Driver specified in the Device section, you won't get the resolution you want. That is a lowest-common-denominator style driver to provide **some** kind of display, whatever happens.

It doesn't look like your card is being detected properly. You'll probably find it useful to know what, exactly, the graphics device that you have in your computer is. You may even find it advantageous if you tell someone here what it is, so that they may help you with configuring it. On the offchance that it is at least an Ati card, using the Ati driver - by putting "ati" in the Driver line of the Device section - may help your card to function better.

Often the monitor information is not passed properly from the graphics card to the X server. Given that your graphics card isn't passing information about **itself** to the X server, it seem quite likely that it is also not passing on information about the monitor. You'll probably find it useful to know what, exactly, the monitor that you have connected to your computer is. You may even find it advantageous if you tell someone here what it is, so that they may help you with configuring it. Given that X is unable to discover information about your monitor itself, it might help to specify for your X server, at a minimum, the refresh rates that your monitor is capable of. This is done by specifying appropriate values for HorizSync and VertRefresh in the Monitor section. This information can often be established from the monitor manual or from the monitor manufacturer's website.

In addition to the VESA modes that your graphics card reports that it is able to do, the X server will also try to configure your display using available modes specified in the xorg.conf Screen section. These may be listed as mode names, for example >         SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
 in which case, refresh rates and other configuration information will be calculated based on the resolution and refresh rate ranges detected or specified, or as modelines which contain all of this configuration information and allow the X server to slavishly apply those settings to the monitor.

If you are unable to put this information adequately into your xorg.conf file, or if you have broken your X server configuration in such a way that it will not start, you may enter much of this information using the xserver-xorg package configuration tool. This is an interactive program that may be run from the command line. It will ask you questions about your hardware, and it will alter your configuration based on the answers you give. This tool may be accessed by using the command **sudo dpkg-reconfigure xserver-xorg**.

Neither your X server, nor anyone here, will be able to configure your computer solely by voodoo. We all need to know what your computer contains to be able to help you to configure it as you wish.

Remember, more information is better than less, and don't be afraid to ask questions and search for information. We're all weirdos who are desperate to help people. If you let us, we'll help you.

---

### Post by olieviya on 2006-11-13
> **CatKiller said:**
> It doesn't look like your card is being detected properly. You'll probably find it useful to know what, exactly, the graphics device that you have in your computer is. You may even find it advantageous if you tell someone here what it is, so that they may help you with configuring it. On the offchance that it is at least an Ati card, using the Ati driver - by putting "ati" in the Driver line of the Device section - may help your card to function better.

It's an ATI 128MB Mobility Radeon X1400 m54-p, the monitor is an alienware (?) I'm on an alienware laptop (m5550).


> **CatKiller said:**
> If you are unable to put this information adequately into your xorg.conf file, or if you have broken your X server configuration in such a way that it will not start, you may enter much of this information using the xserver-xorg package configuration tool. This is an interactive program that may be run from the command line. It will ask you questions about your hardware, and it will alter your configuration based on the answers you give. This tool may be accessed by using the command **sudo dpkg-reconfigure xserver-xorg**.
I have been using the automatic configuration program since before posting, it still won't fix any of my problems. And even when I broke the settings using it, trying to revert back by using it to fix what I had done just didn't seem to get the right results.

> **CatKiller said:**
> Remember, more information is better than less, and don't be afraid to ask questions and search for information. We're all weirdos who are desperate to help people. If you let us, we'll help you.
Ok, well what else can I say when I don't know other info to provide... You now know all I can think of telling, is there anything else? :)
Just ask me because I might be ignorant and not know that you need to know it. Thanks for helping.

EDIT: You might want to check my laptops specs for yourself, check post underneath.

---

### Post by olieviya on 2006-11-13
> **Velotix said:**
> Prove this with a screenshot, please. I ask this because you're not the first person to get the resolution they're after wrong this week. :)

You might actually be after 1280x1024, which is a standard resolution that virtually everything supports these days.
.

Here you go first link is the link to the website i bought my pc from listing it's specs: [http://www.alienware.co.uk/product_detail_pages/Area-51_m5550/area-51m_specs.aspx?SysCode=PC-EU-LT-A51M5550&SubCode=SKU-DEFAULT#pdp-nav](http://www.alienware.co.uk/product_detail_pages/Area-51_m5550/area-51m_specs.aspx?SysCode=PC-EU-LT-A51M5550&SubCode=SKU-DEFAULT#pdp-nav)
And the second is a screenshot of my browser window in winXP: [http://img180.imageshack.us/img180/3562/1280x800hs1.jpg](http://img180.imageshack.us/img180/3562/1280x800hs1.jpg)

---

### Post by olieviya on 2006-11-13
If there are any other questions on what I have tried to do/what hardware I have/software I have used to try and fix this... please ask me because I may not consider something relevant myself and hence leave it out of my posts.

---

### Post by BlackRoseBud on 2006-11-13
Try from a terminal "/etc/X11/xorg.conf" enter, then "sudo gedit xorg.conf then just change all the "Modes" from like ("1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350") to just ("1280x1024")  Then save the file and ctrl+alt+backspace.  After that all options should apear in Systems>Preferences>Screen Resolution.

If you skrew it up just reboot in failsafe by pressing esc when grub starts and selecting failsafe and instead of using gedit use nano to edit the xorg back to the way it was.

Let me know if it helps.

---

### Post by olieviya on 2006-11-13
> **BlackRoseBud said:**
> Try from a terminal "/etc/X11/xorg.conf" enter, then "sudo gedit xorg.conf then just change all the "Modes" from like ("1024x768" "832x624" "800x600" "720x400" "640x480" "640x400" "640x350") to just ("1280x1024")  Then save the file and ctrl+alt+backspace.  After that all options should apear in Systems>Preferences>Screen Resolution.

If you skrew it up just reboot in failsafe by pressing esc when grub starts and selecting failsafe and instead of using gedit use nano to edit the xorg back to the way it was.

Let me know if it helps.

I tried that before... shall i try it again to make sure? Why should I change it to 1280x1024 though? Or did you mean 1280x800?:-?

---

### Post by BlackRoseBud on 2006-11-13
No I mean 1280x1024, because it's worked for me on every machine I've installed Ubuntu 6.06 on.  I don't have to do that with edgy.  Completly remove the other resolutions and add 1280x1024.  Then after you save xorg.conf and reset Xserver (ctrl+alt+backspace) you should see all ther other settings in Systems>Preferences>Screen Resolution.  Even if when you reset Xserver it's at a lower resolution than it was before.

---

### Post by CatKiller on 2006-11-13
> **olieviya said:**
> It's an ATI 128MB Mobility Radeon X1400 m54-p, the monitor is an alienware (?) I'm on an alienware laptop (m5550).

OK. Despite the product page saying 1280x800, [this page]("http://4help.alienware.com/cgi-bin/alienware.cfg/php/enduser/std_adp.php?p_faqid=5173") suggests that the resolution should possibly be **1280x768** instead. It might be worth entering this resolution into your xorg.conf as a mode along with all the others. As the first mode in the list, so that it will be the default if it is available. It's one of those things where people have made their own specifications, and other have made a different specification and called it the same thing: [according to Wikipedia]("http://en.wikipedia.org/wiki/WXGA") WXGA should refer to 1366x768.

Given that [even the manufacturers]("http://www.auo.com/auoDEV/products.php?sec=notebook&func=info&product_id=89&items_id=2") of that screen aren't saying what the HorizSync and VertRefresh numbers should be, it's not surprising that you couldn't find them in your manual. [This Wikipedia page]("http://en.wikipedia.org/wiki/Extended_display_identification_data#Limitations") speculates interestingly on why your X server may not be getting accurate EDID information. You could try adding ```
Option    "IgnoreEDID"    "true"
``` to your **Device** section to tell X to ignore this information entirely and use what you tell it. I **think** that this would mean that you would **have** to provide either estimated screen timings or a valid modeline. It's possible that if you can find more detailed specifications for a monitor that is similar enough to yours that it has the same resolution available, and the same response time, then the HorizSync and VertRefresh values will be close enough to those of your monitor that you will be able to get the resolution you require.

I haven't been able to find confirmation that the "radeon" driver (the one that is called by you putting **Driver "ati"** in your Device section) supports your Mobility Radeon X1400. It's possible that it doesn't yet, and that's why you're not getting a proper Identifier line returned by X. You could try the proprietary [fglrx driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), in case that is newer and supports your device better than the open source ati driver.

> Ok, well what else can I say when I don't know other info to provide... You now know all I can think of telling, is there anything else? :)
Just ask me because I might be ignorant and not know that you need to know it. Thanks for helping.

You've been doing fine. It's more of a general comment that if you know something that could conceivably be helpful then you should mention it, even if you aren't sure that it's necessary information. And similarly that if there's something that you think might be relevant, but you either don't know, or don't know how to find out, then you should mention that too in case someone does know how to get that information. I think you've provided everything that people have specifically asked for so far in this thread, anyway.

You've certainly been helping me push the envelope of my knowledge :)

---

### Post by olieviya on 2006-11-13
> **CatKiller said:**
> OK. Despite the product page saying 1280x800, [this page]("http://4help.alienware.com/cgi-bin/alienware.cfg/php/enduser/std_adp.php?p_faqid=5173") suggests that the resolution should possibly be **1280x768** instead. It might be worth entering this resolution into your xorg.conf as a mode along with all the others. As the first mode in the list, so that it will be the default if it is available. It's one of those things where people have made their own specifications, and other have made a different specification and called it the same thing: [according to Wikipedia]("http://en.wikipedia.org/wiki/WXGA") WXGA should refer to 1366x768.

Hmmm... but in windows it really is 1280*800, I mean look at the screen cap :???: .....of course you may be right and on ubuntu it may need to be a different resolution, i suppose, than winXP.


> **CatKiller said:**
> It's possible that if you can find more detailed specifications for a monitor that is similar enough to yours that it has the same resolution available, and the same response time, then the HorizSync and VertRefresh values will be close enough to those of your monitor that you will be able to get the resolution you require.

I'm sorry, but I have no clue as to how to find a monitor with the same specs as mine... where would you start?

> **CatKiller said:**
> You could try the proprietary [fglrx driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), in case that is newer and supports your device better than the open source ati driver.

Shall I try that one first then? What about what was mentioned above???:confused: 




:biggrin: cheers!

---

### Post by olieviya on 2006-11-13
> **CatKiller said:**
> You could try the proprietary [fglrx driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), in case that is newer and supports your device better than the open source ati driver.

Omg!! Check this out! :twisted: 

[http://img516.imageshack.us/img516/3844/screenshothe3.png](http://img516.imageshack.us/img516/3844/screenshothe3.png)


Thank you very very much.8:mrgreen: :D  :mrgreen:

---

### Post by SRParda on 2006-11-13
For people asking about resolution.
Here is the info send by oliveya, from the X log.
In [COLOR="Gray"](II) VESA(0): Supported additional Video Mode:[/COLOR] line start the info about the mode reported by monitor.
Don't waste time about that. 

But info Min and Max Vertical and Horizontal Frequencies is missing. More info must be in log.

> **SRParda said:**
> You have not post all data for monitor, Min-Max Freq.Horiz. and Min-Max Freq. Vert are needed (data in red)

[QUOTE=olieviya;1747302]Is it somewhere in there? :S

(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.12
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: M54P
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: CPT  Model: 13b1  Serial#: 0
(II) VESA(0): Year: 2006  Week: 21
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.615 redY: 0.332   greenX: 0.315 greenY: 0.561
(II) VESA(0): blueX: 0.152 blueY: 0.127   whiteX: 0.315 whiteY: 0.329
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 813 v_border: 0
(II) VESA(0):  CPT
(II) VESA(0):  CLAA154WA05A
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00056a1
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8

---

### Post by SRParda on 2006-11-13
> **olieviya said:**
> [SIZE="1"][FONT="Courier New"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Option		"XkbLayout"	"gb"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/FONT][/SIZE]

If you have an ati card , why are you using generic vesa driver ?

[COLOR="Gray"]
Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
[COLOR="DarkRed"]Driver "vesa"[/COLOR]
BusID "PCI:1:0:0"
EndSection[/COLOR]

You would must change it to :
[COLOR="Blue"]Driver "radeon"[/COLOR]

And define modeline as I said. But you have to find in log the vertical and horizontal frequencie range for myour monitor, to complete the monitor section.
You must get your frecuencie ranges to add to monitor section 2 lines similar to:
HorizSync 30-64
VertRefresh 56-75
With your monitor frequencies read from X log.

---

### Post by Velotix on 2006-11-13
Ah! Your monitor's widescreen! That explains the odd resolution. Interesting that it's a 16:10 ratio though (widescreen TVs and film are 16:9). **EDIT:** Having tried it out myself, if someone tried to set a 16:9 screen res on a monitor, they'd be trying to set the resolution to have half- and quarter- pixels, which obviously doesn't work.**/EDIT**

Incidentally then, your resolution might still be a bit low - I'm thinking of what would be the widescreen equivalent of 1280x1024, which I suppose would be **1640x1025**. You can always try it as an experiment and see if you like it - it can't hurt, and so long as your monitor can support it - and being an Alienware computer it probably can - you'll get a sharper, better quality picture out of it. Your choice, your PC. ^^

*makes a note of useful widescreen resolutions for future reference*

Widescreen will probably become standard before long - I'm sure it looks great in person because the screencap's pretty cool too!

**EDIT:** For the future reference of everybody, because I'm sure this situation will become more common in future, I've attached a list of equivalent widescreen resolution settings so that everyone knows what they are.

---

### Post by CatKiller on 2006-11-13
> **olieviya said:**
> Omg!! Check this out! :twisted: 

Thank you very very much.8:mrgreen: :D  :mrgreen:

Sweet! Well done olieviya!

Must check out your Deviant Art when I have more time.

---

### Post by olieviya on 2006-11-14
> **CatKiller said:**
> Sweet! Well done olieviya!

Must check out your Deviant Art when I have more time.

Oh, pop round any time :)

---

