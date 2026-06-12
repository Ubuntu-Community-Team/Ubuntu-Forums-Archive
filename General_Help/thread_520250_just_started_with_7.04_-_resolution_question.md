---
title: "just started with 7.04 - resolution question"
date: 2007-08-08
forum: General Help
---

### Post by Marty McFly on 2007-08-08
Hello everyone, this is my first thread here on the Ubuntu forums.

I successfully dual booted my desktop with XP and Fiesty Fawn tonight and I'm happy with everything so far, but one big thing that I've noticed is my max resolution here is 1024x768 when on XP i can go 1200+

Where should I look to fix this?

I have a dell dimension 2350 and I'm using the onboard video card.

---

### Post by windinight on 2007-08-08
that have happened to me and it is weird, but i found an easy solution but a bit "brute" in my system when i boot from the installation cd sometimes it loads with the 1024*768 res and sometimes with the 1280*1024 res, whenever it loads with 1024*768 i just restart most of the time i just have to restart a couple of times :)

---

### Post by southernman on 2007-08-08
> **Marty McFly said:**
> Hello everyone, this is my first thread here on the Ubuntu forums.

I successfully dual booted my desktop with XP and Fiesty Fawn tonight and I'm happy with everything so far, but one big thing that I've noticed is my max resolution here is 1024x768 when on XP i can go 1200+

Where should I look to fix this?

I have a dell dimension 2350 and I'm using the onboard video card.First off, Welcome to the Forum and Ubuntu as well! 

We've been expecting you! ;) jk

Here's what I suggest for your resolution problem:

First step - If you do not know your monitors horizontal and vertical refresh rates... google the model number to find your mfg's website with that information. Write it down to use here in a bit.

Second step - In a terminal run:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```

The first command will simply create a backup of your xorg configuration file.
The second command will drop you into a text based configuration tool to change your video display capabilities. During this process (it isn't hard), just accept the defaults before you get to the section of your screen resolution. Here you will want to choose the "medium" option where you'll be presented with a list of sizes and sync ranges. Use the info you have/know about your monitors abilities and complete this process.

When you reboot, if all went according to plan (and it should) you should be all set.

Hope that's clear.

---

### Post by Marty McFly on 2007-08-09
Okay first screen it asked me to pick the x-server driver so I chose the default (vesa) and hit okay.

Next screen asked me for the identifier for my video card, the default said "generic video card" so I hit okay again.

Next screen said:

> 
Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.                 

Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.                            &#8595;  
 &#9474;                                                         &#8595;  
 &#9474;                                                

...there was an OK option, but when I hit enter nothing happend.  I hit escape to see what would happen and it took me past a bunch of more screens that didn't discuss refresh rate.

Any ideas?

---

### Post by Marty McFly on 2007-08-10
^^^^^

---

### Post by southernman on 2007-08-10
> &#9474; For users of multi-head setups, this option will configure only one of &#9618;
&#9474; the heads. Further configuration will have to be done manually in the X &#9618;
&#9474; server configuration file, /etc/X11/xorg.conf.

Do you have a video card plugged into your bus? Are you just using the onboard video?

Post the output of "lspci" and "lsmod"

---

### Post by Marty McFly on 2007-08-14
> **southernman said:**
> Do you have a video card plugged into your bus? Are you just using the onboard video?

Post the output of "lspci" and "lsmod"

I'm using the onboard video.   Here is lspci:

> 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:06.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


and lsmod:

> 
Module                  Size  Used by
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
i915                   24448  2 
drm                    81044  3 i915
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
container               5248  0 
button                  8720  0 
ac                      6020  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
nls_utf8                3072  2 
ntfs                  107764  2 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
usblp                  14848  0 
i2c_i810                6276  0 
i2c_algo_bit            8712  1 i2c_i810
i2c_core               22656  3 i2c_ec,i2c_i810,i2c_algo_bit
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25244  1 
serio_raw               7940  0 
psmouse                38920  0 
agpgart                35400  3 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  7 
generic                 5124  0 [permanent]
floppy                 59524  0 
ata_piix               15492  5 
b44                    28044  0 
mii                     6528  1 b44
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 usblp,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


Another weird thing that is happening with video is sometimes when I boot up, it doesn't appear correctly, like the top part of the screen is cut off and the OS doesn't take up the entire screen.  I'll reboot and completely shut down trying to fix it and it doesn't look right.  Just sometimes it boots up with normal 1024x768 and sometimes it's all messed up.

---

### Post by southernman on 2007-08-14
Thanks for the output. One more request of you though.
Please post your /etc/X11/xorg.conf file.

edit: What model/brand monitor are you using?

---

### Post by Marty McFly on 2007-08-15
> **southernman said:**
> Thanks for the output. One more request of you though.
Please post your /etc/X11/xorg.conf file.

edit: What model/brand monitor are you using?

xorg.config:

> 
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


I'm using a Compaq CV715 19" CRT monitor.

Weird thing again, my computer restarted overnight because we got a big storm, and the screen loaded up fine in Ubuntu but I couldn't get it to work at all last night.

Still can't do anything higher than 1024x768 though :)

---

### Post by mgpower0 on 2007-08-15
Try this, in a terminal type sudo gedit  /etc/X11/xorg.conf
This will open the x org config file you pasted above but as root user so you can change it.
Your default depth is 16 so in the depth 16 section manually add "1280x1024" so it looks like this
Depth 16
Modes  "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

then save the file- just select save not save as
Log out and back in or reboot to be sure then go to your resolution settings eg- system >preferences>screen resolution and see if 1280x1024 is now an option. If so and it works it should ask if you now want to make that your default resolution

---

### Post by matburton on 2007-08-15
Since you have an i810 chipset you should probably do the following...
1. Make the changes that others have suggested changing the resolution settings in xorg.conf to reflect the real resolutions supported.
2. Open a terminal and use it to download the 915resolution package like this
```

sudo apt-get install 915resolution

```
(This is a work around package for intel chipsets)
3. Log of and then hit CTRL-ALT-Backspace (restarts gdm) and hopefully the resolution should be corrected. If not report back because you can then make changes to the 915reolsution package to help.

Hope that helps!

---

### Post by Marty McFly on 2007-08-27
Not sure what went wrong but my video is all out of whack now.  Sometimes when the OS starts my monitor turns off when the login screen comes up.  Then when I restart it a few times it will come back up.

But when it does, the screen doesn't look right at all.  It's mis-shaped (not square) and the top of the screen is cut off.

Any ideas what to do?  Does my monitor/vid card just not agree with this OS?

---

### Post by Marty McFly on 2007-08-30
anyone?

---

