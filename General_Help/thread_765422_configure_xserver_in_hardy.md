---
title: "configure xserver in hardy"
date: 2008-04-24
forum: General Help
---

### Post by julien-1993 on 2008-04-24
I have just install the fresh release of ubuntu hardy(8.04). However i can't get my screen to a decent resolution.

if i run
```
sudo dpkg-reconfigure xserver-xorg-conf
```
it does not ask for detecting vid card nor ask for resolution and refresh rate like it used to do in gutsy(7.10)

I then try the gui in system->preferences->screen resolution, it does not offer the refresh rate that i used to have wich is 85hz, only weird things like 68hz and 50hz.

i also tried
```
sudo displayconfig-gtk
```
wich does not help more.

everything was working perfectly in gutsy when i configure it with dpkg-reconfigure. i would like to achieve same result. please help

---

### Post by Mikecore on 2008-04-24
please post output of

```


>lspci

and 

>lsmod


```

---

### Post by julien-1993 on 2008-04-24
heres for lspci
```
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
03:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
```

and for lsmod
```
Module                  Size  Used by
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
loop                   18948  0 
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           146880  4 snd_emu10k1_synth
snd_ac97_codec        101028  1 snd_emu10k1
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10500  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4868  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
analog                 13600  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
nvidia               7825536  34 
serio_raw               7940  0 
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
psmouse                40336  0 
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
emu10k1_gp              4608  0 
pcspkr                  4224  0 
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gameport               16008  3 analog,emu10k1_gp
snd                    56996  20 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
evdev                  13056  4 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
button                  9232  0 
i2c_nforce2             7680  0 
i2c_core               24832  2 nvidia,i2c_nforce2
nvidia_agp              9628  1 
agpgart                34760  2 nvidia,nvidia_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
pata_amd               14212  2 
ohci1394               33584  0 
libata                159344  3 ata_generic,pata_acpi,pata_amd
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
ohci_hcd               25348  0 
forcedeth              51980  0 
usbcore               146028  4 usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
```

---

### Post by Wiebelhaus on 2008-04-24
Same issue here , My old reliable commands aren't working.

---

### Post by Odd-rationale on 2008-04-24
This is crazy. What happened to sudo dpkg-reconfigure xserver-xorg??? Doesn't give as many options as it used to.

also in the xorg file, what is "Configured Video Device", "Configured Monitor" etc ?? Where is it "configured"?

---

### Post by Mikecore on 2008-04-24
please post output

```


sudo less /etc/X11/xorg.conf


```

---

### Post by julien-1993 on 2008-04-24
here is my xorg.conf except that i played a bit in it
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Philips"
	Modelname	"Philips 107B(17inch/CM6800)"
	Horizsync	30.0-69.0
	Vertrefresh	50.0-130.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x960@85"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by Odd-rationale on 2008-04-24
> **Mikecore said:**
> please post output

```


sudo less /etc/X11/xorg.conf


```
Here it is:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by Mikecore on 2008-04-24
try the command that is listed in xorg.conf

```


 sudo dpkg-reconfigure -phigh xserver-xorg


```

you might want to read the xorg.conf file yourself so you know what your doing.

---

### Post by julien-1993 on 2008-04-24
ok i did try what u suggested, but it give a real simple xorg.conf with "configured setting" as an argument in much of the section.

now im stuck in 640*480.....

dont tell me ill have to reinstall gutsy, save my xorg.conf and reinstall hardy again....this can not be the real solution....

at the point i'am with the fresh xorg.conf generated with the -phyg option, i only have the choices of 640*480 and 800*600 in the screen resolution gui.

---

### Post by Odd-rationale on 2008-04-24
I think I remember reading somewhere that they tried to make the new xorg "easier to configure"...

---

### Post by riskbreaker927 on 2008-04-24
It's highly likely the problems in this thread are being caused by the ones in the following:

[http://ubuntuforums.org/showthread.php?t=761447](http://ubuntuforums.org/showthread.php?t=761447)

---

### Post by julien-1993 on 2008-04-24
I found out a solution to configure my xserver.

Install package nvidia-setings and make the xorg.conf with it. (there is options in it to do so)

this is not a normal way of doing it imho, but ill use it for now since they decide to make things complicated

---

### Post by schtufbox on 2008-04-24
> **julien-1993 said:**
> I found out a solution to configure my xserver.

Install package nvidia-setings and make the xorg.conf with it. (there is options in it to do so)

this is not a normal way of doing it imho, but ill use it for now since they decide to make things complicated

That's what I did. I can't believe they released hardy with xorg like this, it's not as if they didn't know, it happened to loads of people in beta...
Ah well, it's the only problem I've had with Hardy all the way through beta to release (same install just updated each time) so I won't whine too much :)

---

### Post by rplantz on 2008-04-25
> **julien-1993 said:**
> I found out a solution to configure my xserver.

Install package nvidia-setings and make the xorg.conf with it. (there is options in it to do so)

Thank you!

Pretty weird. And synaptic indicates that nvidia-settings isn't even supported. Oh well, just a minor glitch in what has been a very smooth upgrade otherwise.

---

