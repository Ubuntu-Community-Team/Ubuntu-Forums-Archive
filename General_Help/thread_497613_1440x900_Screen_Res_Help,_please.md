---
title: "1440x900 Screen Res Help, please?"
date: 2007-07-10
forum: General Help
---

### Post by Uncle Spellbinder on 2007-07-10
I have an Envision G918w1 19" widescreen monitor.  On Feisty, the most available is 1280x1024. Everything is a bit scrunched.  Any ideas on how to enable 1440x900?  I did a search, and found no answers.

Any help appreciated.

lspci output, if it helps:

```
unclespellbinder@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 13)
05:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
```

---

### Post by Dr. Octagon on 2007-07-10
I don't know much about resolution settings, but I have 1440x900 running on a Nvidia NVS 110m on my laptop.  Hopefully this stuff helps.

```
doc-oc@ubuntu:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 110M / GeForce Go 7300 (rev a1)

03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


```

And my xorg:

```
Section "Monitor"

    Identifier     "Generic Monitor"

    HorizSync       28.0 - 72.0

    VertRefresh     43.0 - 60.0

    Option         "DPMS"

    Option         "MonitorLayout" "CRT,LFP"

    Option         "Clone" "true"

EndSection



Section "Device"

    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"

    Driver         "nvidia"

EndSection



Section "Screen"

    Identifier     "Default Screen"

    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"

    Monitor        "Generic Monitor"

    DefaultDepth    24

    Option         "AddARGBVisuals" "True"

    Option         "AddARGBGLXVisuals" "True"

    Option         "NoLogo" "True"

    Option         "TwinView" "True"

    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"

    SubSection     "Display"

        Depth       1

        Modes      "1440x900"

    EndSubSection

    SubSection     "Display"

        Depth       4

        Modes      "1440x900"

    EndSubSection

    SubSection     "Display"

        Depth       8

        Modes      "1440x900"

    EndSubSection

    SubSection     "Display"

        Depth       15

        Modes      "1440x900"

    EndSubSection

    SubSection     "Display"

        Depth       16

        Modes      "1440x900"

    EndSubSection

    SubSection     "Display"

        Depth       24

        Modes      "1440x900"

    EndSubSection

EndSection


```

I thought I'd also add that I have twinview enabled so that I can utilize a projector, and I also have Compiz Fusion installed.  Hope this helps

---

### Post by NilsE on 2007-07-10
I am guessing that since it is an Intel chip you are probably running either the vesa or i810 driver.  And since it is an Intel chip the new Intel driver might help.

So, go into synaptic and search for the Intel video driver and try it.  Worst case, you go back to whichever one was installed.  You will know since it will ask to uninstall it.

Oh yeah, you can then change the driver to intel in the xorg.conf file

But it would be better to go into a terminal and run

sudo dpkg-reconfigure -phigh xserver-xorg

to recreate the xorg.conf file

---

### Post by fragos on 2007-07-10
Regardless of what resolutions we place in xorg.conf, the driver will determine which resolutions it's willing to use.  If the driver called out in xorg is "vesa" you can't get 1440x900.  Insure that the driver is "i810" and that 1440x900 is called out as a resolution option.  As an example, the appropriate xorg.conf sections that require to changed are included as they apear on my PC.  The fields in question are in red.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"**[COLOR="Red"]nvidia[/COLOR]**"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Viewsonic VA1912wb"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Viewsonic VA1912wb"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		**[COLOR="Red"]"1440x900"[/COLOR]** "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by jwh400 on 2007-07-10
To get 1440x900 to appear as a choice I had to edit my /etc/X11/xorg.conf file.
Back that file up first then scroll down and enter your resolution to the beginning of each line and remember the quotes and space.

[IMG]http://www.yesalbum.com/v001/jwane/Screenshots/resolution.png[/IMG]

---

### Post by Uncle Spellbinder on 2007-07-11
Well, I had 1440x900.  Ended up with a large black bar on the left of the screen taking up about a quarter of the screen. Since this was a fresh install (via Wubi), I re-installed anew to try again. 

Seeing so many screen resolution issues on the forums here, I gotta ask.  Is this a driver issue or an Ubuntu issue? Either way, I'll continue to try. I may just end up having to use Ubuntu in the least distracting resolution until something easier/workable comes along.  I've tried the suggestions above (as well as several others in other threads).  The best I got so far was a 1440x900 resolution with the big black bar. :(

---

### Post by MrObvious on 2007-07-11
Post your xorg.conf file please.

---

### Post by Uncle Spellbinder on 2007-07-11
> **MrObvious said:**
> Post your xorg.conf file please.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by fragos on 2007-07-11
Are you sure you want 1440x1440 and not 1440x900?

---

### Post by Uncle Spellbinder on 2007-07-11
> **fragos said:**
> Are you sure you want 1440x1440 and not 1440x900?

As I said, that was from a fresh, stock install.  I've updated it to reflect the 1440x900 (see my post above).  I've also made sure the  **Intel i8xx, i9xx display driver** is, indeed, installed. Clicking "screen resolution" shows no entry for 1440x900.  I'm at a loss. :confused:

---

### Post by Uncle Spellbinder on 2007-07-13
Anyone?

---

### Post by fragos on 2007-07-13
At this stage, I can only guess.  I'd remove the 1440x1440 since I don't believe it's a valid resolution option.

---

### Post by Uncle Spellbinder on 2007-07-13
Hmmm.  Appreciate the help, Just did that, rebooted.  No effect.  I'm completely stumped.  Getting late, gonna sleep on it.  Maybe something will come to me in a dream.  ;)

Unfortunately, that dream will probably be in 1280x1024. :?

---

### Post by Uncle Spellbinder on 2007-07-13
Well, here is my current *xorg.conf*, and no luck getting 1440x900.  That option does not show in Screen Resolution. I'm slowly pulling my hair out! :confused:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by iota on 2007-07-13
You can add it as an entry into your xorg by doing the following.

Type **sudo gtf 1440 900 85**

Then copy the results into the 'monitor' section of your xorg. Now go to the 'screen' section and under Depth 24 add a reference to "1440x900_85". Kill x using ctrl+alt+backspace and it should be at 1440x900, or 1440x900 should be an option at least.

Hope this helps, I kinda typed it off the top of my head so if any thing's wrong I apologise and hope someone can correct me :P

Good luck.

---

### Post by Uncle Spellbinder on 2007-07-13
Appreciate the tip! Thanks.  Since you're not 100% sure, I'll wait for confirmation before I continue.

Again, thanks.

---

### Post by Uncle Spellbinder on 2007-07-13
> **iota said:**
> You can add it as an entry into your xorg by doing the following.

Type **sudo gtf 1440 900 85**

Then copy the results into the 'monitor' section of your xorg. Now go to the 'screen' section and under Depth 24 add a reference to "1440x900_85". Kill x using ctrl+alt+backspace and it should be at 1440x900, or 1440x900 should be an option at least.

Hope this helps, I kinda typed it off the top of my head so if any thing's wrong I apologise and hope someone can correct me :P

Good luck.

Well, these are the results:

```
unclespellbinder@ubuntu:~$ sudo gtf 1440 900 85
Password:

  # 1440x900 @ 85.00 Hz (GTF) hsync: 80.33 kHz; pclk: 156.79 MHz
  Modeline "1440x900_85.00"  156.79  1440 1536 1696 1952  900 901 904 945  -HSync +Vsync
```

You say "Then copy the results into the 'monitor' section of your xorg."  What part of the results?  Where in the "monitor" section? As far as Modeline, Do I just add "1440x900_85.00"  or everything after Modeline above?

---

### Post by metallicamaster3 on 2007-07-13
here you are: [http://ubuntu.mysillypc.com/showthread.php?p=84#post84](http://ubuntu.mysillypc.com/showthread.php?p=84#post84)

---

### Post by Uncle Spellbinder on 2007-07-13
> **metallicamaster3 said:**
> here you are: [http://ubuntu.mysillypc.com/showthread.php?p=84#post84](http://ubuntu.mysillypc.com/showthread.php?p=84#post84)
Thanks for the link, though I'm a bit confused.  Which do I do? *sudo gtf 1440 900 85* as stated by iota, or *sudo gtf 1440 900 75* as stated in the link you provided?  Or does it matter?

**EDIT:**
I see the post in the link you supplied was just edited from  *sudo gtf 1440 900 [color=#990000]75[/color]* to *sudo gtf 1440 900 [color=#990000]60[/color]*.  A bit *more* confused.

**EDIT again:**
I see..."Adjust these settings for the max your monitor can do."

---

### Post by iota on 2007-07-13
That's down to preference, tiz just the refresh rate setting. Higher is normally regarded as better, but there is really not much difference between 75 and 85hz.

60 I would not advise using though, going that low will probably hurt your eyes and give you headaches if you use your computer very much.

Hope you get it all sorted.

---

### Post by Mostlyharmless42 on 2007-07-13
ok, i didn't read all of the posts, so you may have already gotten this solution.  I had the same problem and all i did was replace all instances of 1440x1440 with 1440x900 in the xorg.conf save that and reboot.  it just rebooted at a nice clean 1440x900 if not try the screen resolution list, it should appear there. I hope this helps.

---

### Post by Uncle Spellbinder on 2007-07-13
Following the link, I pasted it as such:

```
Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
# 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
  Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync
EndSection
```

No effect.

---

### Post by Uncle Spellbinder on 2007-07-13
> **Mostlyharmless42 said:**
> ok, i didn't read all of the posts, so you may have already gotten this solution.  I had the same problem and all i did was replace all instances of 1440x1440 with 1440x900 in the xorg.conf save that and reboot.  it just rebooted at a nice clean 1440x900 if not try the screen resolution list, it should appear there. I hope this helps.

Did that, no effect.

---

### Post by iota on 2007-07-13
What was the reference to it you posted in the screen section? 1440x900_75.00?

---

### Post by fragos on 2007-07-13
With CRT displays the faster frequencies are desirable but aren't an issue with LCD displays which don't have the flicker issue at lower frequencies.  60 is fine for LCD displays.

---

### Post by Uncle Spellbinder on 2007-07-14
> **iota said:**
> What was the reference to it you posted in the screen section? 1440x900_75.00?

I referenced *1440x900_75*

And as I'm on an LCD 19" Widescreen, perhaps 60 should be tried.

---

### Post by Uncle Spellbinder on 2007-07-14
OK, here's my current xorg.conf (still no luck):

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900 @ 60.00" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by iota on 2007-07-14
> Modes		"1440x900 @ 60.00"

That should be **"1440x900_60.00"**

With any luck that should work now, everything else looks fine.

---

### Post by Uncle Spellbinder on 2007-07-14
> **iota said:**
> That should be **"1440x900_60.00"**

With any luck that should work now, everything else looks fine.

And, *still*..........no luck.  I'm starting to go a bit nuts:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by pxwpxw on 2007-07-14
Something else to try.

I found the spec for G918W1 WideScreen LCD (VIS 19")
here:
[http://www.envisiondisplay.com/products/specsheets/g918w1-specs.pdf]("http://www.envisiondisplay.com/products/specsheets/g918w1-specs.pdf")

1. In the modeline: 
  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

You might have to change that to +Hsync -Vsync (see the spec, not very clear). Or just omit them from the modeline (man xorg.conf says they are optional)
 
2. In the monitor section add the HorizSync 30-81 VertRefresh	55-75

Section "Monitor"
	Identifier "G918w1"
	Option "DPMS"
	HorizSync	30-81
	VertRefresh	55-75
# try it without the modeline first, 
#  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
#  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  +HSync -Vsync
EndSection

---

### Post by ldrn on 2007-07-14
It sounds to me like this might be a well-known issue with the Intel i810 driver -- my laptop had a very similar issue.  If it is, you can't fix it by using xorg.conf -- you need to get and install 915resolution... I'll include instructions here just in case it is the issue.

*edit* I found out someone else already did a great write-up of this and even made a script to make using it easier:
[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html]("http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html")

If this *is* a problem with your i810 intel card (and by the way, there's a newer "intel" driver that you might need to turn on prereleases to see -- it has the package xserver-xorg-video-intel) that'll fix it.

---

### Post by Uncle Spellbinder on 2007-07-14
Thanks, ldrn.   I did try *915resolution* and I ended up with large black bar on the left of the screen.  Also tried *xserver-xorg-video-intel* and the sasme black bar occurred. 

I'll check your link when I get home from work, hope it helps.

---

### Post by Uncle Spellbinder on 2007-07-15
I guess I'll just have to settle for 1280x1024.  Shame that something as seemingly simple as 1440x900 screen resolution has proved to be such an impossible task.

---

### Post by longlegs on 2007-07-15
Hi ,
 I may be asking a dumb question but consider this. 
Early on in this thread you had 1440x900 resolution but a black bar was on the left side of the screen. 
Have you tried getting back to this condition and USE the MONITOR controls to move the display left and make it wider???
Good luck
longlegs

---

### Post by Uncle Spellbinder on 2007-07-15
> **longlegs said:**
> Hi ,
 I may be asking a dumb question but consider this. 
Early on in this thread you had 1440x900 resolution but a black bar was on the left side of the screen. 
Have you tried getting back to this condition and USE the MONITOR controls to move the display left and make it wider???
Good luck
longlegs

Tried that.  It only moves the screen right.  Like the black bar on the left is an obstacle. However, when using 1440x900, I find that when I go to Screen Resolution and change from 60 Hz to 75 Hz and then "apply", an "out of range" notification comes up from the monitor. I then select go "use  previous resolution" (bringing it back to 60 Hz) and the black bar on the left is gone and the screen is *perfect*.  I have to do this every time I logon to Feisty in order to have 1440x900 with no black bar on the left.

In other words, with 1440x900 at 60 Hz, I get the black bar on the left.  Switching to 75 Hz and back to 60 Hz, the bar is gone and the screen displays 1440x900 just fine.

---

### Post by longlegs on 2007-07-15
Hi !
I just realised that I have a similar problem in that on normal boot, I wind up with a good screen except for a 1/2 inch rectangle at the upper left, which goes away after a few screen switches. This only occurs with 1024x768 which is my needed resolution.
Sorry I coud not help.
Hope you have good luck with yours.
longlegs

---

### Post by fragos on 2007-07-15
> **Uncle Spellbinder said:**
> Tried that.  It only moves the screen right.  Like the black bar on the left is an obstacle. However, when using 1440x900, I find that when I go to Screen Resolution and change from 60 Hz to 75 Hz and then "apply", an "out of range" notification comes up from the monitor. I then select go "use  previous resolution" (bringing it back to 60 Hz) and the black bar on the left is gone and the screen is *perfect*.  I have to do this every time I logon to Feisty in order to have 1440x900 with no black bar on the left.

In other words, with 1440x900 at 60 Hz, I get the black bar on the left.  Switching to 75 Hz and back to 60 Hz, the bar is gone and the screen displays 1440x900 just fine.

This really sounds like a driver problem.  It's almost as if something isn't properly initialized when the driver is loaded.  You should summarize you findings and file a bug.  Nothing like this occurs with my Nvidia based video.  I'm reasonably sure that 60 is the correct frequency.  LCD images have a longer persistence than CRT images which eliminates the flicker that slower frequency rates create with CRTs.

---

### Post by ldrn on 2007-07-15
> **Uncle Spellbinder said:**
> Tried that.  It only moves the screen right.  Like the black bar on the left is an obstacle. However, when using 1440x900, I find that when I go to Screen Resolution and change from 60 Hz to 75 Hz and then "apply", an "out of range" notification comes up from the monitor. I then select go "use  previous resolution" (bringing it back to 60 Hz) and the black bar on the left is gone and the screen is *perfect*.  I have to do this every time I logon to Feisty in order to have 1440x900 with no black bar on the left.
While this is definitely a glitch and a bad thing, it doesn't sound that painful -- you could use xrandr and a script to do that automatically whenever you log in. (Sorry if I'm belaboring something obvious to you -- I just thought I'd mention it just in case!)

---

### Post by Uncle Spellbinder on 2007-07-15
I've tried all the suggestions here (and elsewhere) to no avail. As I said earlier, with 1440x900 at 60 Hz, I get the black bar on the left. Switching to 75 Hz and back to 60 Hz, the bar is gone and the screen displays 1440x900 just fine. It seems that's the way I'll have to do it, unless I purchace a video card and try again with that. Damn.  :(

---

### Post by pxwpxw on 2007-07-16
In page 1 post#6, you reported having 1440x900 with the black bar left side of screen, and still have that black bar problem. This seems to be just a horizontal sync/blanking timing problem, so you get the black bar from either incorrect timing in the modeline that the driver is using, or from the monitor horizontal sync at the wrong point.
Switching from 75Hz to 60Hz might somehow be forcing the correct sync and timing.

So there are a few things that might help track it down:
1. Can you post a copy of /var/log/Xorg.0.log after restarting to the 1440x900 black bar case.
2. Does the screen lose any of the right side of the picture when it has the black bar at the left (i.e. is the whole picture just shifted to the right)
3. Are there any settings/connections on the monitor to select video sync (hsync polarity +-  composite sync ... )
4. In the modeline in xorg.conf there is the -HSync  +VSync
The alternatives include +HSync and I think "csync", all of which affect the timing as well as the numbers in the modeline.
But 915resolution may override the xorg.conf modeline, however the Xorg.0.log should show what is actually being used.

I am having another look at this, may have missed something.

---

### Post by Uncle Spellbinder on 2007-07-16
> **pxwpxw said:**
> In page 1 post#6, you reported having 1440x900 with the black bar left side of screen, and still have that black bar problem. This seems to be just a horizontal sync/blanking timing problem, so you get the black bar from either incorrect timing in the modeline that the driver is using, or from the monitor horizontal sync at the wrong point.
Switching from 75Hz to 60Hz might somehow be forcing the correct sync and timing.

So there are a few things that might help track it down:
1. Can you post a copy of /var/log/Xorg.0.log after restarting to the 1440x900 black bar case.
2. Does the screen lose any of the right side of the picture when it has the black bar at the left (i.e. is the whole picture just shifted to the right)
3. Are there any settings/connections on the monitor to select video sync (hsync polarity +-  composite sync ... )
4. In the modeline in xorg.conf there is the -HSync  +VSync
The alternatives include +HSync and I think "csync", all of which affect the timing as well as the numbers in the modeline.
But 915resolution may override the xorg.conf modeline, however the Xorg.0.log should show what is actually being used.

I am having another look at this, may have missed something.



Thanks for the input/help.  I won't be at my computer until morning (it's 12:30am here in the Altanta area). Working graveyard tonight.  I'll post back info then.  Thanks, again.  ;)

I can say that as far as No. 2 is concerned, the whole picture just shifted to the right.

---

### Post by pxwpxw on 2007-07-16
I am installing feisty on a MacBook c2d right now, after trying 915resolution with the Desktop i386 CD. I used the debian package. It appeared to work by adding a 1280x800 (for MacBook) mode, but I was unable to get the i810 driver to use that mode, so now going to see what happens for an installed system and how to get it going. I think the modeline setting and all that stuff in xorg.conf is probably irrelevant, I could not get that to make any difference, it just kept running 1024x768.
Will post results.

---

### Post by Uncle Spellbinder on 2007-07-16
Have since re-installed (via Wubi) Ubuntu Feisty.  Using the newer intel driver as the i810 did nothing.  Here is my current xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Still suffering from the same black bar issue.

**/var/log/Xorg.0  after switching from 60 to 75 and back to 60 (no black bar on left):**

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 16 12:34:58 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "G918w1"
(**) |   |-->Device "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 107b,5053 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2582 card 107b,5053 rev 04 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,2668 card 107b,5053 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2666 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 107b,5053 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 107b,5053 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 107b,5053 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 107b,5053 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 107b,5053 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 107b,5053 rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4351 card 107b,5053 rev 13 class 02,00,00 hdr 00
(II) PCI: 05:01:0: chip 14f1,2f20 card 14f1,2000 rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x50300000 - 0x503fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x50100000 - 0x501fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x50400000 - 0x504fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:3), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x50500000 - 0x505fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0x50200000/19, 0x40000000/28, 0x50280000/18, I/O @ 0xffe0/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[1] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[2] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[3] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[4] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[5] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[6] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[7] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[10] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[11] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[12] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[13] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[14] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[15] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[21] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[22] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[23] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[24] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[1] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[2] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[3] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[4] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[5] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[6] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[7] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[10] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[11] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[12] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[13] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[14] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[15] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[21] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[22] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[23] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[24] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[16] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[17] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[18] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[19] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[20] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[21] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[27] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[28] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[29] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[30] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 14.94.94
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[16] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[17] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[18] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[19] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[20] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[21] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[27] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[28] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[29] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[30] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[19] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[20] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[21] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[22] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[23] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[24] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[30] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[31] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[32] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[33] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x50200000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (410, 260) mm
(**) intel(0): DPI set to (89, 140)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x50280000 - 0x502bffff (0x40000) MS[B]
	[1] 0	0	0x40000000 - 0x4fffffff (0x10000000) MS[B]
	[2] 0	0	0x50200000 - 0x5027ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[8] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[9] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[10] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[11] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[12] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[13] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] 0	0	0x0000ffe0 - 0x0000ffe7 (0x8) IS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[23] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[24] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[25] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[26] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[27] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[28] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[34] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[35] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[36] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[37] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1472 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x00037fff: xaa scratch (64 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x0402f000 physical)
(II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x20060000 physical)
(II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x047c9000 physical)
(II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x20048000 physical)
(II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x04002000 physical)
(II) intel(0): 0x007d0000-0x03cc7fff: front buffer (54240 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (11520 kB)
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (11520 kB)
(II) intel(0): 0x06000000-0x07ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x08000000-0x09ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf9370000
(II) intel(0): [drm] mapped SAREA 0xf9370000 to 0xb7b88000
(II) intel(0): [drm] framebuffer handle = 0x407d0000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0x50200000
(II) intel(0): [drm] ring buffer = 0x40000000
(II) intel(0): [drm] init sarea width,height = 1440 x 1440 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x180fa000
(II) intel(0): [drm] Back Buffer = 0x44000000
(II) intel(0): [drm] Depth Buffer = 0x45000000
(II) intel(0): [drm] textures = 0x48000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0x40000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x007c0000 (pgoffset 1984)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007c4000 (pgoffset 1988)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x007c5000 (pgoffset 1989)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x007c9000 (pgoffset 1993)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x007d0000 (pgoffset 2000)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 8 at 0x08000000 (pgoffset 32768)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 410 x 257
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
```

**/var/log/Xorg.0  Leaving it at 60 (black bar on left visible):**
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 16 13:07:50 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "G918w1"
(**) |   |-->Device "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 107b,5053 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2582 card 107b,5053 rev 04 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,2668 card 107b,5053 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2666 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 107b,5053 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 107b,5053 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 107b,5053 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 107b,5053 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 107b,5053 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 107b,5053 rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4351 card 107b,5053 rev 13 class 02,00,00 hdr 00
(II) PCI: 05:01:0: chip 14f1,2f20 card 14f1,2000 rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x50300000 - 0x503fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x50100000 - 0x501fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x50400000 - 0x504fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:3), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x50500000 - 0x505fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0x50200000/19, 0x40000000/28, 0x50280000/18, I/O @ 0xffe0/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[1] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[2] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[3] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[4] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[5] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[6] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[7] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[10] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[11] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[12] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[13] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[14] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[15] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[21] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[22] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[23] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[24] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[1] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[2] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[3] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[4] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[5] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[6] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[7] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[10] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[11] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[12] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[13] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[14] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[15] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[21] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[22] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[23] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[24] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[16] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[17] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[18] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[19] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[20] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[21] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[27] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[28] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[29] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[30] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 14.94.94
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[16] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[17] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[18] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[19] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[20] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[21] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[27] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[28] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[29] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[30] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[19] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[20] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[21] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[22] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[23] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[24] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[30] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[31] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[32] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[33] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x50200000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (410, 260) mm
(**) intel(0): DPI set to (89, 140)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x50280000 - 0x502bffff (0x40000) MS[B]
	[1] 0	0	0x40000000 - 0x4fffffff (0x10000000) MS[B]
	[2] 0	0	0x50200000 - 0x5027ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[8] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[9] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[10] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[11] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[12] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[13] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] 0	0	0x0000ffe0 - 0x0000ffe7 (0x8) IS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[23] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[24] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[25] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[26] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[27] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[28] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[34] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[35] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[36] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[37] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1472 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x00037fff: xaa scratch (64 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x22525000 physical)
(II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x22480000 physical)
(II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x2252b000 physical)
(II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x22484000 physical)
(II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x22530000 physical)
(II) intel(0): 0x007d0000-0x03cc7fff: front buffer (54240 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (11520 kB)
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (11520 kB)
(II) intel(0): 0x06000000-0x07ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x08000000-0x09ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf931e000
(II) intel(0): [drm] mapped SAREA 0xf931e000 to 0xb7b16000
(II) intel(0): [drm] framebuffer handle = 0x407d0000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0x50200000
(II) intel(0): [drm] ring buffer = 0x40000000
(II) intel(0): [drm] init sarea width,height = 1440 x 1440 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x180fa000
(II) intel(0): [drm] Back Buffer = 0x44000000
(II) intel(0): [drm] Depth Buffer = 0x45000000
(II) intel(0): [drm] textures = 0x48000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0x40000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x007c0000 (pgoffset 1984)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007c4000 (pgoffset 1988)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x007c5000 (pgoffset 1989)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x007c9000 (pgoffset 1993)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x007d0000 (pgoffset 2000)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 8 at 0x08000000 (pgoffset 32768)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 410 x 257
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
```

---

### Post by pxwpxw on 2007-07-16
That looks interesting  I have just put 915resolution on the MacBook here, and
after running it manually, it gave me the 1280x800 32bit that I wanted and was unable to get as installed - only 1024x768.  I did not have to edit my xorg.conf and it has no modelines.
I will take  a good look tomorrow and compare with your Xorg.0.log and post my conf. Maybe an answer there.
I am about ready for a sleep its 3:30 am here.

---

### Post by Uncle Spellbinder on 2007-07-16
Thanks so much for you help in this issue.  Off to work (1:40 pm here).

---

### Post by DarkPontiac on 2007-07-16
Your missing the refresh rates on your xorg.conf. I run off an ATi Radeon 9250 PCI with an Integrated i845GL card (that is disabled) and when reinstalled my ubuntu today, it was stuck in 640x480...

What i say was the monitor only contained this.

----
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection
----

When i added,

----
	HorizSync 28-72
	VertRefresh 43-60
----

To make it look like 

----
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync 28-72
	VertRefresh 43-60
EndSection
----

It booted into 1440x900. Maybe you can try adding this and see if it works for you.

---

### Post by Uncle Spellbinder on 2007-07-17
I now have added refresh rates and modeline.  Still get the black bar on the left of the screen (sing-on screen as well). My current xorg.conf is set as follows:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
HorizSync 30-81
VertRefresh 55-75
# try it without the modeline first,
# # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 +HSync -Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by pxwpxw on 2007-07-17
Hi, just getting back to it now.
Could you please run and post
```

 sudo 915resolution -l

```

That is if you have installed 915resolution.

Edit:

This might be the answer - in your Xorg.0.log there are 3 intel(0): Modelines "1440x900" for 75 Hz and for 60 Hz
The first one 136.75 is for 75Hz, the other 2 are for 60 Hz (you can check using gtf )

 75Hz -- (II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
 60Hz -- (II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
 60Hz -- (II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync

The difference is in the interval from the right end of the picture video at 1440 to the start of the next line at 1936 for 75Hz, compared with 1904 for 60Hz, and also in the sync at 1536-1688.

So if you use the 75Hz modeline you should get 75Hz and some difference in the picture shift, but I am not sure if you are able to use 75Hz (it is within in the monitor spec that I posted earlier). If you must use 60Hz, the numbers need changing.

However, I have to say I can't tell from the Xorg.0.log just which modeline is being used, or which colour depth they apply to, there seems to be something missing from the tail end of the logs.

In xorg.conf  a modeline needs to  be "1440x900" to match the Section "Screen" Modes and to match the Xorg.0.log mode names from the driver and video card, i.e. "1440x900_60" won't work. My mistake in using that straight from gtf.

You are getting 1440x900 modelines in Xorg.0.log, but I dont know if you are using the 915resolution utility. It  might be a good idea to try it to clear up some of the mystery.

I dont think PCintel or Macintel makes any difference here, its the intel i810 drivers and 915 chipset series.

---

### Post by Uncle Spellbinder on 2007-07-17
I'm not using the *xserver-xorg-video-i810* driver or *915 resolution*.  I'm using the newest intel driver, *xserver-xorg-video-intel*. Do I need to change the DefaultDepth	24 entry from *1440x900_60.00* back to *1440x900*?


gtf output:

60
```
unclespellbinder@ubuntu:~$ gtf 1440 900 60

  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
```

75
```
unclespellbinder@ubuntu:~$ gtf 1440 900 75

  # 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
  Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync
```


**EDIT:**

Tried it as such, no luck. Using 75, my monitor says "out of range" so it seems 60 is necessarry. 

```
Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
HorizSync 30-81
VertRefresh 55-75
# try it without the modeline first,
# # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection
```

---

### Post by Uncle Spellbinder on 2007-07-17
Installed 915 Resolution for the purpose of getting the output of * sudo 915resolution -l*.  

Hmmmm.  I don't see 1440x900 anywhere:

```
unclespellbinder@ubuntu:~$  sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
unclespellbinder@ubuntu:~$ 
```

---

### Post by pxwpxw on 2007-07-17
What I dont understand is  - where/how are you selecting between 60 and 75Hz. Then if we understand that, can go from there. You need to keep referring to the latest Xorg.0.log each time you try something to see if it had any effect, its a trial and error process to a large extent to get it to do what you intend. 

For the Modeline names, yes you need to be using the consistent names and same as appearing in the modes list for the driver and chip, which you get from the log, that is my understanding. It is a bit unclear, but thats why the log is important. I will have a look at the new driver info.
The value of the 915resolution package is that it make it clear what the mode name will be and can set the resolution so it is known. I believe it can apply to your new driver, and you are still using a chip from the 915 family.

OK just saw your other post, you now need to add a 1440 900 32 mode using 915resolution, it has a man page and if you run 
```

 dpkg -L 915resolution

```
That will list all it's files, you can read how it is used, there is a small howto, I will try to find  a link and explain.

---

### Post by Uncle Spellbinder on 2007-07-17
> **pxwpxw said:**
> What I dont understand is  - where/how are you selecting between 60 and 75Hz. Then if we understand that, can go from there.

Changing between 60 and 75Hz using the screen provided when clicking system > preferences > screen resolution.

---

### Post by Uncle Spellbinder on 2007-07-17
> **pxwpxw said:**
> ...
OK just saw your other post, you now need to add a 1440 900 32 mode using 915resolution, it has a man page and if you run 
```

 dpkg -L 915resolution

```
That will list all it's files, you can read how it is used, there is a small howto, I will try to find  a link and explain.

Just read the readme file.  Doesn't seem to explain how to add amode, though.

Interesting link here [**915Resolution: Intel Video BIOS Hack**](http://www.geocities.com/stomljen/) provided from the Synaptic entry for 915Resolution.

---

### Post by pxwpxw on 2007-07-17
I used the debian i386 915resolution package.
/usr/share/doc/915resolution/README.Debian explains how to set the new mode to work at restart.

I ran this manually to replace the highest numbered mode (5c) by the mode I wanted for my MacBook which is 1280 800 32
but in xorg.conf it is "1280x800" and depth is 24

```

 sudo 915resolution 5c 1280 800 32

## Then checked the result
 sudo 915resolution -l

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
### .... other modes 
Mode 5c : 1280x800, 32 bits/pixel

```

Then restart the X server by Control-Alt-Del (on a MacBook this works).

Then open the new /var/log/Xorg.0.log (check the date/time to make sure the X server restarted)
and the list of 915 modes should include this one, ( this may not be permanent across restarts unless you do it by editing 
 /etc/default/915resolution )

*Mode: 5c (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007723
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0x40000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000

There is no timing information here, so that is where I think you may need a modeline in xorg.conf.

I did not bcause this information is extracted from the display insterface on the MacBook.

---

### Post by Uncle Spellbinder on 2007-07-17
I did *sudo 915resolution 5c 1440 900 32* - restarted - did *sudo 915resolution -l*.

I'm now seing 1440x900!  Still have the black bar, but at least 1440x900 is listed.

```
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1440x900, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1440x900, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1440x900, 32 bits/pixel
unclespellbinder@ubuntu:~$ 
```

Not sure how to proceed from here, but I've got a positive result, at least.  Got to go to work, I'll check back tonight on this thread and the readme file.  :mrgreen:

---

### Post by Uncle Spellbinder on 2007-07-17
Edited */etc/default/915resolution* to reflect the changes.  Stil no-go.

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
```

Off to work.  Appreciate your assistance!

---

### Post by Uncle Spellbinder on 2007-07-17
After another restart, 1440x900 seems gone:

```
unclespellbinder@ubuntu:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
unclespellbinder@ubuntu:~$ 
```

---

### Post by pxwpxw on 2007-07-17
If you have these files, then to retain the new mode after restarting you may need to edit /etc/default/915resolution
as in README.Debian.

Checkout Xorg.0.log to see if the new mode is in there after restart.

Then the xorg.conf modeline may need work, or it may not. 

$ dpkg -L 915resolution
/.
/etc
/etc/acpio
/etc/acpi/resume.d
/etc/acpi/resume.d/49-915-resolution-set.sh
/etc/default
/etc/default/915resolution
/etc/init.d
/etc/init.d/915resolution
/usr
/usr/sbin
/usr/sbin/915resolution
/usr/share
/usr/share/doc
/usr/share/doc/915resolution
/usr/share/doc/915resolution/changelog.gz
/usr/share/doc/915resolution/chipset_info.txt
/usr/share/doc/915resolution/README.Debian
/usr/share/doc/915resolution/copyright
/usr/share/doc/915resolution/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/915resolution.8.gz
/etc/acpi/resume.d/13-915-resolution-set.sh
$ 

$ cat /etc/default/915resolution 
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
# MODE=auto
# auto might not work, try it later
MODE=5c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
###end of file

---

### Post by pxwpxw on 2007-07-18
> **Uncle Spellbinder said:**
> Edited */etc/default/915resolution* to reflect the changes.  Stil no-go.

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
```

Off to work.  Appreciate your assistance!

You need to change it to **MODE=5c**

**auto** only works for some systems with support for that.

Next time you post could you tell me for the black bar, what  %  screen width (measure it).
But if you get that 915resolution running at restart it may fix it.

edit:

in the Xorg.0.log lists of intel modelines, there are 3 for 1440x900, all slightly different.
When you open the desktop "Screen Resolution Preferences" does the  drop down Resolution and Refresh rate show more 1440x900  options and have you tried them all?
I'm thinking it may relate to the 3 in the log.

---

### Post by Uncle Spellbinder on 2007-07-18
Well, still have the black bar. Measuring my screen-
* Viewable: a little more than 16 inches  wide including black bar
* Black bar alone: a little more than 2 1/2 inches wide.

I found that commenting out the modeline in xorg.conf gave me a centered logoff screen (the Ubuntu logo when shutting down). Before that, it was all scrunched to the lower right of the screen. Other than that, nothing's changed.

Current */etc/default/915resolution*
```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
```

Current *xorg.conf*
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
HorizSync 30-81
VertRefresh 55-75
# try it without the modeline first,
# # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
# Modeline "1440x900"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Uncle Spellbinder on 2007-07-18
> **pxwpxw said:**
> n the Xorg.0.log lists of intel modelines, there are 3 for 1440x900, all slightly different.
When you open the desktop "Screen Resolution Preferences" does the  drop down Resolution and Refresh rate show more 1440x900  options and have you tried them all?
I'm thinking it may relate to the 3 in the log.

One entry for 1440x900 and it includes 60 and 75 Hz. As I said previously, when I boot, it's at 1440x900 at 60 Hz with the black bar.  When I change from 60 to 75 and back to 60, the black bar is gone and all is well. Restarting, the same scenario happens all over again.  When leaving it at 75, the monitor shows a message "out of range" that is constant, does not dissappear.

---

### Post by pxwpxw on 2007-07-18
OK, forget that idea. Press on with the 915resolution.

---

### Post by pxwpxw on 2007-07-18
Forget the "screen resolution" desktop menu, look in X0rg.0.log to see if there are some new mode listings in there, see my earlier post for the type of stuff I get, and recheck with 915resolution -l to make sure its is effective. We are aiming to get control by a modeline in xorg.conf if that is possible, so we can adjust the picture horizontal displacementt. At this stage just looking for something that indicates progress in that direction.

---

### Post by Uncle Spellbinder on 2007-07-18
Well, I geuss I'll just have to go through the motions of switching from 60 to 75 and back on each boot for the time being. At least I get the proper screen after doing that.  I'm at a loss.  All seems set up to work, yet it doesn't.  Maybe something will come to me in the future.

Appreciate you help, pxwpxw.


EDIT

Just saw your post.  I'll try looking at that.

---

### Post by hessiess on 2007-07-18
you could just give up and get a cheep nvidia card.:popcorn:

i have a small resolution problem, although i can live with it...

---

### Post by pxwpxw on 2007-07-18
I missed your post #60, its relevant, need a while to think. But whatever else, you do you need to get the 915resolution to be running, that is essential for the 915 chip, the intel drivers dont do that they still need help.

---

### Post by Uncle Spellbinder on 2007-07-18
> **pxwpxw said:**
> I missed your post #60, its relevant, need a while to think. But whatever else, you do you need to get the 915resolution to be running, that is essential for the 915 chip, the intel drivers dont do that they still need help.

Okee Dokee  ;) 

Again, Thanks!

---

### Post by fragos on 2007-07-18
I've been following this post for some time.  My experience is with a Viewsonic 1440x900 LCD and an Nvidia FX5200.  I'm wondering if the 32 bit color depth might be your problem.  I'd try 24 to see what happens.  I let my system select the frequency and it uses 50.  I've an excellent flicker free display.

---

### Post by Uncle Spellbinder on 2007-07-19
> **fragos said:**
> I've been following this post for some time.  My experience is with a Viewsonic 1440x900 LCD and an Nvidia FX5200.  I'm wondering if the 32 bit color depth might be your problem.  I'd try 24 to see what happens.  I let my system select the frequency and it uses 50.  I've an excellent flicker free display.

Gave it a shot, no-go. Appreciate the input, though.

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
[color=#CC0000]BIT=24[/color]
```

---

### Post by pxwpxw on 2007-07-19
If you want to continue the quest for 1440x900 here is what I think. You need to use 915resolution.

1. The 915resolution package may not have been fully configured to make 1440x900 available from your 915 Chip at system restart, you should have had some more positive results by now. Possibly there are some files missing.
 
What package did you install?
To confirm that everything is there, post the output from
```

 sudo find / -name '*915*'

```

2. Your xorg.conf has accumulated some doubltful changes (some due to me). You can generate a clean version using
```

 sudo dpkg-reconfigure -phigh xserver-xorg

```
You should only need to select your intel driver, and the 1440x900 resolution and the 1280x???? which is currently working, it will default to that. It will save a backup of your existing xorg.conf. You should not need to edit xorg.conf.

3. When you think 915resolution is running, post another Xorg.0.log, that should show some confirmation.

4. The monitor onscreen setup might show what resolution it is running as a check.

---

### Post by Uncle Spellbinder on 2007-07-19
> **pxwpxw said:**
> If you want to continue the quest for 1440x900 here is what I think. You need to use 915resolution.

1. The 915resolution package may not have been fully configured to make 1440x900 available from your 915 Chip at system restart, you should have had some more positive results by now. Possibly there are some files missing.
 
What package did you install?
To confirm that everything is there, post the output from
```

 sudo find / -name '*915*'

```

2. Your xorg.conf has accumulated some doubltful changes (some due to me). You can generate a clean version using
```

 sudo dpkg-reconfigure -phigh xserver-xorg

```
You should only need to select your intel driver, and the 1440x900 resolution and the 1280x???? which is currently working, it will default to that. It will save a backup of your existing xorg.conf. You should not need to edit xorg.conf.

3. When you think 915resolution is running, post another Xorg.0.log, that should show some confirmation.

4. The monitor onscreen setup might show what resolution it is running as a check.

I installed the 915 resolution package via synaptic. 

```
unclespellbinder@ubuntu:~$ sudo find / -name '*915*'
Password:
/lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/i915.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/char/drm/i915.ko
/usr/lib/dri/i915_dri.so
/usr/lib/dri/i915tex_dri.so
/usr/share/foomatic/db/source/printer/Epson-Stylus_Photo_915.xml
/usr/share/doc/915resolution
/usr/share/man/man8/915resolution.8.gz
/usr/sbin/915resolution
/usr/src/linux-headers-2.6.20-16-generic/include/config/drm/i915.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/drm/i915.h
/var/cache/fontconfig/21a99156bb11811cef641abeda519a45-x86.cache-2
/var/cache/apt/archives/915resolution_0.5.2-10ubuntu1_i386.deb
/var/lib/dpkg/info/915resolution.postinst
/var/lib/dpkg/info/915resolution.list
/var/lib/dpkg/info/915resolution.md5sums
/var/lib/dpkg/info/915resolution.prerm
/var/lib/dpkg/info/915resolution.conffiles
/var/lib/dpkg/info/915resolution.postrm
/var/lib/scrollkeeper/TOC/915
/var/lib/scrollkeeper/index/915
/etc/rc4.d/S12915resolution
/etc/rc0.d/K12915resolution
/etc/rc5.d/S12915resolution
/etc/rc2.d/S12915resolution
/etc/acpi/resume.d/13-915-resolution-set.sh
/etc/acpi/resume.d/49-915-resolution-set.sh
/etc/default/915resolution~
/etc/default/915resolution
/etc/rc3.d/S12915resolution
/etc/rc1.d/K12915resolution
/etc/init.d/915resolution
/etc/rc6.d/K12915resolution
/proc/irq/17/i915@pci:0000:00:02.0
/sys/module/i915
/home/unclespellbinder/.thumbnails/normal/aa23fbb574915867c031ffe57b1bb73b.png
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP34/A0012915.properties
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP34/A0007915.properties
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP35/A0013915.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP38/A0014915.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009154.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009150.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009151.dll
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009152.properties
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009153.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009155.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009156.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009157.ico
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009158.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP39/A0009159.manifest
/media/Projects/System Volume Information/_restore{F845E3DB-F751-4BE4-A620-64F2CA1BFB5F}/RP43/A0020915.manifest
/media/My Book/System Volume Information/_restore{D6C77ED5-39E6-4076-A37B-A97CAA40B5BD}/RP267/A0033915.manifest
/media/My Book/System Volume Information/_restore{D6C77ED5-39E6-4076-A37B-A97CAA40B5BD}/RP267/A0034915.manifest
/media/My Book/System Volume Information/_restore{D6C77ED5-39E6-4076-A37B-A97CAA40B5BD}/RP268/A0035915.properties
/media/My Book/System Volume Information/_restore{D6C77ED5-39E6-4076-A37B-A97CAA40B5BD}/RP271/A0036915.dll
/media/My Book/System Volume Information/_restore{D6C77ED5-39E6-4076-A37B-A97CAA40B5BD}/RP276/A0039915.manifest
/media/My Book/System Volume Information/_restore{D6C77ED5-39E6-4076-A37B-A97CAA40B5BD}/RP278/A0041915.manifest
```

After diong *sudo dpkg-reconfigure -phigh xserver-xorg*, this is my xorg.conf.  All I need to change is the driver from 'i810" to "intel" and add 1440x900 to all the modes under *display* in *Screen* ?

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Uncle Spellbinder on 2007-07-19
> **pxwpxw said:**
> The monitor onscreen setup might show what resolution it is running as a check.

Clicking the "information" option on my monitor -

*with black bar visible (scrunched screen, black bar on left) -*
```
H.Frequency - 56.07 kHz
V.Frequency - 60.03 Hz
Pixel Clock - 89.60 MHz
Resolution - 1440x900
```

*with no black bar (after switching from 60 to 75 and back)* -
```
H.Frequency - 55.94 kHz
V.Frequency - 59.89 Hz
Pixel Clock - 106.62  MHz
Resolution - 1440x900
```

Regarding xorg.conf, I've made only 2 changes:  changed the "i810" driver to "intel" and added "1440x900" to all the modes under *display* in *Screen*. Currently, xorg.conf looks like this:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G918w1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"G918w1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x160"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Uncle Spellbinder on 2007-07-20
Well, it looks as if I'll need to wait until I can try with another video card.  Nothing seems to work. I'll just have to use Feisty as-is for the time being. Thanks to *pxwpxw*, and everyone else, for trying to help.

---

### Post by fragos on 2007-07-20
I'd recommend that the vidia card be some flavor of Nvidia, 7000 series or prior.  My FX 5200 performs well, is inexpensive and works great with my 1440x900 LCD.  Nvidia drivers appear to be more stable than ATI.

---

### Post by pxwpxw on 2007-07-21
> **Uncle Spellbinder said:**
> Clicking the "information" option on my monitor -

*with black bar visible (scrunched screen, black bar on left) -*
```
H.Frequency - 56.07 kHz
V.Frequency - 60.03 Hz
Pixel Clock - 89.60 MHz
Resolution - 1440x900
```

*with no black bar (after switching from 60 to 75 and back)* -
```
H.Frequency - 55.94 kHz
V.Frequency - 59.89 Hz
Pixel Clock - 106.62  MHz
Resolution - 1440x900
```

/code]

I think you've got it now, your post#72, the monitor information. There is nothing wrong with your 915 card, just a problem with the startup sequence for xwindows and 915resolution, possibly due to your video setup being non-standard.

When you restart Linux from scratch, the X server is starting up before 915resolution has time to make the 1440x900 availabe.

When you switch from 60 to 75 Hz, and then revert back the Xserver restarts and this time 1440x900 is available. 

You should be able to get the same result, instead of switching 60/75, just do Control-Alt-Del to restart the xserver.

If this is correct the rest is easy, just needs a small fix to the startup sequence, I can give you that one. But to prove the point post a copy of /var/log/Xorg.0.log after getting the good screen, whichever way you get it.

---

### Post by Uncle Spellbinder on 2007-07-21
Using the "good screen", here is my */var/log/Xorg.0.log*:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 21 12:02:45 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "G918w1"
(**) |   |-->Device "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 107b,5053 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2582 card 107b,5053 rev 04 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,2668 card 107b,5053 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2666 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 107b,5053 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 107b,5053 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 107b,5053 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 107b,5053 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 107b,5053 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 107b,5053 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 107b,5053 rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4351 card 107b,5053 rev 13 class 02,00,00 hdr 00
(II) PCI: 05:01:0: chip 14f1,2f20 card 14f1,2000 rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x50300000 - 0x503fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x50100000 - 0x501fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x50400000 - 0x504fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:3), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x50500000 - 0x505fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0x50200000/19, 0x40000000/28, 0x50280000/18, I/O @ 0xffe0/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[1] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[2] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[3] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[4] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[5] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[6] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[7] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[10] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[11] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[12] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[13] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[14] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[15] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[21] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[22] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[23] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[24] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[1] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[2] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[3] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[4] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[5] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[6] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[7] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[10] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[11] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[12] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[13] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[14] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[15] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[21] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[22] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[23] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[24] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[16] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[17] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[18] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[19] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[20] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[21] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[27] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[28] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[29] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[30] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 14.94.94
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[16] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[17] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[18] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[19] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[20] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[21] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[27] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[28] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[29] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[30] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[5] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[6] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[7] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[8] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[9] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[19] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[20] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[21] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[22] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[23] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[24] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[30] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[31] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[32] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[33] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x50200000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (410, 260) mm
(**) intel(0): DPI set to (89, 140)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x50280000 - 0x502bffff (0x40000) MS[B]
	[1] 0	0	0x40000000 - 0x4fffffff (0x10000000) MS[B]
	[2] 0	0	0x50200000 - 0x5027ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x50000000 - 0x5000ffff (0x10000) MX[B]
	[8] -1	0	0x50100000 - 0x50103fff (0x4000) MX[B]
	[9] -1	0	0x502c4000 - 0x502c43ff (0x400) MX[B]
	[10] -1	0	0x502c0000 - 0x502c3fff (0x4000) MX[B]
	[11] -1	0	0x50280000 - 0x502bffff (0x40000) MX[B](B)
	[12] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[13] -1	0	0x50200000 - 0x5027ffff (0x80000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] 0	0	0x0000ffe0 - 0x0000ffe7 (0x8) IS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x00001007 (0x8) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[23] -1	0	0x000030a0 - 0x000030af (0x10) IX[B]
	[24] -1	0	0x000030e8 - 0x000030eb (0x4) IX[B]
	[25] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[26] -1	0	0x000030ec - 0x000030ef (0x4) IX[B]
	[27] -1	0	0x000030c8 - 0x000030cf (0x8) IX[B]
	[28] -1	0	0x000030b0 - 0x000030bf (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[34] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[35] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[36] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[37] -1	0	0x0000ffe0 - 0x0000ffe7 (0x8) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1472 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x00037fff: xaa scratch (64 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x1bd0d000 physical)
(II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x1bd14000 physical)
(II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x1bd13000 physical)
(II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x1bd38000 physical)
(II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x1bd1d000 physical)
(II) intel(0): 0x007d0000-0x03cc7fff: front buffer (54240 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (11520 kB)
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (11520 kB)
(II) intel(0): 0x06000000-0x07ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x08000000-0x09ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf9393000
(II) intel(0): [drm] mapped SAREA 0xf9393000 to 0xb7bce000
(II) intel(0): [drm] framebuffer handle = 0x407d0000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0x50200000
(II) intel(0): [drm] ring buffer = 0x40000000
(II) intel(0): [drm] init sarea width,height = 1440 x 1440 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x180fa000
(II) intel(0): [drm] Back Buffer = 0x44000000
(II) intel(0): [drm] Depth Buffer = 0x45000000
(II) intel(0): [drm] textures = 0x48000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0x40000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x007c0000 (pgoffset 1984)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007c4000 (pgoffset 1988)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x007c5000 (pgoffset 1989)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x007c9000 (pgoffset 1993)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x007d0000 (pgoffset 2000)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 8 at 0x08000000 (pgoffset 32768)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 410 x 257
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) XAA: Evicting pixmaps
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
(II) intel(0): Modeline "256x144"    2.75  256 264 288 320  144 147 152 155 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
(II) intel(0): Modeline "1440x900"  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync
(II) intel(0): EDID vendor "EPI", prod id 6468
```

Off to work, I'll check back on this thread tonight.  THANKS!

---

### Post by pxwpxw on 2007-07-22
Can you confirm that you can get the "good screen" just by doing the xserver restart 
 ( control-alt-del ), without doing the 60/75 switch?

In any case, please post output from this for info to change your startup sequence settings.
```

 ls /etc/rc?.d

```
(That is a question mark not a seven)

---

### Post by Wipboy on 2007-07-22
I'm on the same mission with my viewsonic wide screen, not having 1440x900 is not very pleasing. :(. I'm followed this post up until the end, yet I can't edit my xorg file.

---

### Post by Uncle Spellbinder on 2007-07-22
> **pxwpxw said:**
> Can you confirm that you can get the "good screen" just by doing the xserver restart 
 ( control-alt-del ), without doing the 60/75 switch?

In any case, please post output from this for info to change your startup sequence settings.
```

 ls /etc/rc?.d

```
(That is a question mark not a seven)

To restart xserver, I  do control-alt-backspace (control-alt-delete does nothing). In any event, If I restart xserver without doing the 60/75 switch, the screen goes black, restarts and I'm back at the logon screen (black bar and all).  So it seems to have no effect.


ls /etc/rc?.d:
```
unclespellbinder@ubuntu:~$ ls /etc/rc?.d
/etc/rc0.d:
K01gdm            K50alsa-utils                       S30urandom
K01splashy        README                              S31umountnfs.sh
K01usplash        S01cpkernel                         S32umounthost
K12915resolution  S01linux-restricted-modules-common  S40umountfs
K19hplip          S10fixsendsigs                      S60umountroot
K20apport         S15wpa-ifupdown                     S90halt
K25hwclock.sh     S20sendsigs                         S99killntfs3g

/etc/rc1.d:
K01gdm      K12915resolution  K20apport         K20powernowd  K90sysklogd
K01usplash  K19cupsys         K20dbus           K20rsync      README
K11anacron  K19hplip          K20hotkey-setup   K21acpid      S30killprocs
K11atd      K20acpi-support   K20makedev        K74bluetooth  S90single
K11cron     K20apmd           K20nvidia-kernel  K89klogd

/etc/rc2.d:
README                       S19cupsys         S89anacron
S05vbesave                   S19hplip          S89atd
S10acpid                     S20apmd           S89cron
S10powernowd.early           S20apport         S90binfmt-support
S10sysklogd                  S20hotkey-setup   S98usplash
S10xserver-xorg-input-wacom  S20makedev        S99acpi-support
S11klogd                     S20nvidia-kernel  S99rc.local
S12915resolution             S20powernowd      S99rmnologin
S12dbus                      S20rsync          S99stop-readahead
S13gdm                       S25bluetooth

/etc/rc3.d:
README                       S19cupsys         S25bluetooth
S05vbesave                   S19hplip          S89anacron
S10acpid                     S20apmd           S89atd
S10sysklogd                  S20apport         S89cron
S10xserver-xorg-input-wacom  S20hotkey-setup   S90binfmt-support
S11klogd                     S20makedev        S98usplash
S12915resolution             S20nvidia-kernel  S99acpi-support
S12dbus                      S20powernowd      S99rc.local
S13gdm                       S20rsync          S99rmnologin

/etc/rc4.d:
README                       S19cupsys         S25bluetooth
S05vbesave                   S19hplip          S89anacron
S10acpid                     S20apmd           S89atd
S10sysklogd                  S20apport         S89cron
S10xserver-xorg-input-wacom  S20hotkey-setup   S90binfmt-support
S11klogd                     S20makedev        S98usplash
S12915resolution             S20nvidia-kernel  S99acpi-support
S12dbus                      S20powernowd      S99rc.local
S13gdm                       S20rsync          S99rmnologin

/etc/rc5.d:
README                       S19cupsys         S25bluetooth
S05vbesave                   S19hplip          S89anacron
S10acpid                     S20apmd           S89atd
S10sysklogd                  S20apport         S89cron
S10xserver-xorg-input-wacom  S20hotkey-setup   S90binfmt-support
S11klogd                     S20makedev        S98usplash
S12915resolution             S20nvidia-kernel  S99acpi-support
S12dbus                      S20powernowd      S99rc.local
S13gdm                       S20rsync          S99rmnologin

/etc/rc6.d:
K01gdm            K50alsa-utils                       S30urandom
K01splashy        README                              S31umountnfs.sh
K01usplash        S01cpkernel                         S32umounthost
K12915resolution  S01linux-restricted-modules-common  S40umountfs
K19hplip          S10fixsendsigs                      S60umountroot
K20apport         S15wpa-ifupdown                     S90reboot
K25hwclock.sh     S20sendsigs                         S99killntfs3g

/etc/rcS.d:
README                              S30checkfs.sh
S01mountkernfs.sh                   S35mountall.sh
S01readahead                        S36mountall-bootclean.sh
S02hostname.sh                      S39readahead-desktop
S03splashy                          S40networking
S06keyboard-setup                   S45waitnfs.sh
S07linux-restricted-modules-common  S46mountnfs-bootclean.sh
S08loopback                         S49console-setup
S10udev                             S50hwclock.sh
S11mountdevsubfs.sh                 S55dns-clean
S13pcmciautils                      S55pppd-dns
S15module-init-tools                S70screen
S17procps.sh                        S70x11-common
S20checkroot.sh                     S80bootmisc.sh
S22mtab.sh                          S85urandom
S25brltty                           S90console-screen.sh
```

---

### Post by fragos on 2007-07-22
> **Wipboy said:**
> I'm on the same mission with my viewsonic wide screen, not having 1440x900 is not very pleasing. :(. I'm followed this post up until the end, yet I can't edit my xorg file.

xorg.conf is owned by root and users only have read only access.  There are a number of ways to solve this but this may be simplest for you.  In a terminal window do "gksudo gedit /etc/X11/xorg.conf".  This will open xoerg.conf as root.  You will be prompted for a password, use your user password.

---

### Post by Wipboy on 2007-07-23
> **fragos said:**
> xorg.conf is owned by root and users only have read only access.  There are a number of ways to solve this but this may be simplest for you.  In a terminal window do "gksudo gedit /etc/X11/xorg.conf".  This will open xoerg.conf as root.  You will be prompted for a password, use your user password.

I broke xconf, to where it didn't start the splash screen, after playing with for a while and following some threads in the forum I got it to work. I had to select the driver over again and load the backup file...I think that's how it went, either way..when I came back to the desk top 1440x900 has available. Now my desktop looks clean and crisp as it should. Thanks guys. :)

---

### Post by pxwpxw on 2007-07-23
> **Uncle Spellbinder said:**
> To restart xserver, I  do control-alt-backspace (control-alt-delete does nothing). In any event, If I restart xserver without doing the 60/75 switch, the screen goes black, restarts and I'm back at the logon screen (black bar and all).  So it seems to have no effect.


Well, looks like I was wrong. I can see no evidence there that 915resolution has any effect with the intel driver, so there is no point in adjusting its startup. 

I installed the xserver-xorg-video-intel package here, on the MacBook, to see what happened, and with the "intel" driver. It does not matter what modes are shown by <915resolution -l> in particular with no 915 1280x800 mode, the intel driver somehow manages to run 1280x800 which is ths native LCD screen here on the MacBook (corresponding to your 1440x900). Which just confirms what you have been reporting since you installed the intel driver.

Previously when using the i810 driver, I needed 915resolution, but not with the intel driver. I am using the MacBook 945 Video chip and a laptop integrated screen, you have a 915 chip and an external screen, so its a bit hard to judge if that is significant. Unfortunately I cant reproduce a bad screen result here no matter what I do, I dont have a problem.
I dont know if you would get any different results by reverting back to the I810 driver and running 915resolution, I doubt it.
 
I see reference lines LoadModule "vm86* and "intel(0) VESA BIOS   detected"  in my Xorg.0.log, I dont think that appears in yours.

I tried all sorts of variations in xorg.conf for display resolution and modelines, with no effect whatever. In the Section "Screen" I reduced it down to simply Identifier, Device, and Monitor, with no DefaultDepth and no SubSection "Display", it still worked. 

The xubuntu desktop Display Preferences Setting I have here are showing a selection of resolutions plus "Default", all of which work (from 640x480 to 1280x1280) but the actual monitor screen remains at 1280x800.
However I cannot find where these settings are controlled from, some configuration setting somewhere, but not xorg.conf. 

From your monitor information option reading, the good screen is running the correct 1440x900 with Pixel Clock 106 MHz, this also seems to be one of the modelines shown in your intel driver Xorg.0.log, and you can only get it using your Desktop Display Setting by switching to 75Hz which fails, then back to 60Hz which changes to the correct settings. So if someone can say where that good setting comes from, it should be possible to make it the startup configuration - but this is not in xorg.conf, it is somwhere in the desktop  and its applications.

All of which doesn't help you much but it might encourage someone else to provide an answer about the Display Settings configuration.

In short, I give up.:confused:

---

### Post by Uncle Spellbinder on 2007-07-23
> **pxwpxw said:**
> ...In short, I give up.:confused:
I really appreciate your attempts at helping me with this issue.  I think, short of getting a PCI graphics card, I'll just need to muddle through as-is.  


Thanks again.   ;)

---

### Post by Uncle Spellbinder on 2007-07-26
Since my computer is a a tad on the older side (2 years old), I only have one available PCI slot (no AGP or PCI-E). I'm finding my choices limited. I really prefer Nvidia over ATI.  ATI driver support for Linux and Vista seem lacking at best.

I found this: [**BFG NVIDIA GeForce 6200 OC 256MB PCI**](http://www.bfgstore.com/ProductDetails.asp?ProductCode=BFGR62256OCP)

Seems like it should do the job for Ubuntu as well as Vista.

---

### Post by pikul on 2007-07-26
I didnt read all the thread but did you install the XSERVER-XORG-VIDEO-INTEL driver ? my new HP monitor is 19" widescreen and uses the exact same resolution, that driver fixed it, all i did was reconfigure my xorg to the i810 driver, un-install it and then install this one, i have an intel 950 chipset :)

---

### Post by Uncle Spellbinder on 2007-07-27
915 here.  Tried the XSERVER-XORG-VIDEO-INTEL driver to no avail.

---

### Post by w4ett on 2007-07-27
Shot in the dark here...just had a thought....

what is the output of:
```

xrandr
```

from the terminal/CLI

---

### Post by Uncle Spellbinder on 2007-07-27
> **w4ett said:**
> Shot in the dark here...just had a thought....

what is the output of:
```

xrandr
```

from the terminal/CLI


```
unclespellbinder@ubuntu:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1440 x 900    ( 411mm x 261mm )  *60   75  
 1   1280 x 1024   ( 411mm x 261mm )   75   60  
 2   1280 x 960    ( 411mm x 261mm )   60  
 3   1152 x 864    ( 411mm x 261mm )   75  
 4   1024 x 768    ( 411mm x 261mm )   75   70   60  
 5    832 x 624    ( 411mm x 261mm )   75  
 6    800 x 600    ( 411mm x 261mm )   72   75   60   56  
 7    640 x 480    ( 411mm x 261mm )   75   73   67   60  
 8    720 x 400    ( 411mm x 261mm )   70  
 9   1440 x 1440   ( 411mm x 261mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none
unclespellbinder@ubuntu:~$
```

```
unclespellbinder@ubuntu:~$ cli
Usage is: mono [options] program [program-options]

Development:
    --aot                  Compiles the assembly to native code
    --debug                Enable debugging support
    --profile[=profiler]   Runs in profiling mode with the specified profiler module
    --trace[=EXPR]         Enable tracing, use --help-trace for details
    --help-devel           Shows more options available to developers

Runtime:
    --config FILE          Loads FILE as the Mono config
    --verbose, -v          Increases the verbosity level
    --help, -h             Show usage information
    --version, -V          Show version information
    --runtime=VERSION      Use the VERSION runtime, instead of autodetecting
    --optimize=OPT         Turns on or off a specific optimization
                           Use --list-opt to get a list of optimizations
    --security             Turns on the security manager (unsupported, default is off)
unclespellbinder@ubuntu:~$
```

---

### Post by w4ett on 2007-07-27
Well.....xorg does see your 1440x900 res...Hmmm   Here's an interesting read on changing your resolutions on the fly:

[http://www.debian-administration.org/articles/201](http://www.debian-administration.org/articles/201)

I believe the command will be:
```

xrandr --size 1440x900

```

---

### Post by pxwpxw on 2007-07-27
> **w4ett said:**
> Well.....xorg does see your 1440x900 res...Hmmm   Here's an interesting read on changing your resolutions on the fly:

[http://www.debian-administration.org/articles/201](http://www.debian-administration.org/articles/201)

I believe the command will be:
```

xrandr --size 1440x900

```

Or
xrandr -s 0

Certainly works here, with 945 chip and intel driver on MacBook, also the selection of resolutions from "xrandr -q" correspond exactly with the selections avaiable from the Desktop "Display Preferences" menu. 
Hope it works for the OP.
.

---

