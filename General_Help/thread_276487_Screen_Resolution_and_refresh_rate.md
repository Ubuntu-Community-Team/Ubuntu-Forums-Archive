---
title: "Screen Resolution and refresh rate"
date: 2006-10-13
forum: General Help
---

### Post by pluto1111 on 2006-10-13
[SIZE="3"]I cannot get my screen resolution to 1024 X 768 @ 85 hz (the best I can do is 1024 X 768 @ 75 hz). I'm using a Spectrum 9Glr monitor, and an Intel i740 video card. I reconfigured xserver, and below is what I have set in my xorg.conf file.
Please help!

Thank you.[/SIZE]

```
Section "Monitor"
	Identifier	"AOC Spectrum 9Glr"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i740"
	Monitor		"AOC Spectrum 9Glr"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

```

---

### Post by adwait on 2006-10-13
You probably don't have the correct drivers...

---

### Post by bewire on 2006-10-13
Hello, I use Ubuntu 6.06 LTS and have problems with setting screen resolution and refresh rate. The picture is kind of blurry / flimmering like if I can see the display refreshing

Video Card: Ati Radeon 9800 XXL , AMD Athlon 64 3000+ 

Where can I find the relevant documentation for configuring the video card ? Tried /etc/x11/xorg.conf, but the system responded " /etc/x11/xorg.conf: No such file or directory"

Thanks :-)

lspci listing:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge  (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890  South]
0000:00:06.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadca st Decoder (rev 01)
0000:00:07.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Pri sm Xbow] (rev 01)
0000:00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
0000:00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/ K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 98 00 XT]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)

---

### Post by Crooksey on 2006-10-13
> **bewire said:**
> Hello, I use Ubuntu 6.06 LTS and have problems with setting screen resolution and refresh rate. The picture is kind of blurry / flimmering like if I can see the display refreshing

Video Card: Ati Radeon 9800 XXL , AMD Athlon 64 3000+ 



```

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --overlay-type=Xv

```

Then reboot

---

### Post by pluto1111 on 2006-10-13
If I don't have the right drivers installed, where can I find the right drivers for the Intel i740 video card?  I have the CD that came with the card, but it is for Windows.

---

### Post by bewire on 2006-10-13
Thanks !!! I had the linux-restricted-modules so I just added xorg-driver-fglrx and sudo aticonfig --overlay-type=Xv. The display is now stable, but it looks like it's pixelated a bit at 1024x768 75 hz (I had a crystal clear display with Debian, but can't remember the settings ...) Can I fix this with aticonfig ?

---

### Post by bewire on 2006-10-14
> **bewire said:**
> Thanks !!! I had the linux-restricted-modules so I just added xorg-driver-fglrx and sudo aticonfig --overlay-type=Xv. The display is now stable, but it looks like it's pixelated a bit at 1024x768 75 hz (I had a crystal clear display with Debian, but can't remember the settings ...) Can I fix this with aticonfig ?

Hi, after rebooting the display looks good :-) Thanks again !

bewire

---

### Post by bewire on 2006-10-14
> **bewire said:**
> Hi, after rebooting the display looks good :-) Thanks again !

bewire

Ooops ... I was maybe a bit too optimistic :-) Graphics and images are still "pixelated" and the fonts are "ugly" at some pages ... But they look good here at forum. 

bewire

---

### Post by bewire on 2006-10-15
> **bewire said:**
> Ooops ... I was maybe a bit too optimistic :-) Graphics and images are still "pixelated" and the fonts are "ugly" at some pages ... But they look good here at forum. 

bewire

I forgot to mention that I have a hp1502 LCD monitor.

Here is the contents of my xorg.conf:

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
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "no"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "ATI RADEON 9800 XT"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "hp L1502"
        Option          "DPMS"
        HorizSync       30-60
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI RADEON 9800 XT"
        Monitor         "hp L1502"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by CatKiller on 2006-10-15
System -> Preferences -> Fonts has the option for sub-pixel smoothing, that may make text look better on your LCD screen.

---

### Post by bewire on 2006-10-15
> **CatKiller said:**
> System -> Preferences -> Fonts has the option for sub-pixel smoothing, that may make text look better on your LCD screen.

Thanks, done that. But I still have a problem with graphics and images. Looks like they are aliased (pixelated edges) ...

Please see the screenshot. In my display the Ubunto logo and folder icons are   aliased and kind of blurry I think.

After reading different forum posts related to video drivers I've noted the issue with image "banding". Actually the conclusion for most of the posts is that banding is not the problem but the video drivers ... But I'm not sure where that leaves me.

bewire

---

### Post by igknighted on 2006-10-15
> **bewire said:**
> Hello, I use Ubuntu 6.06 LTS and have problems with setting screen resolution and refresh rate. The picture is kind of blurry / flimmering like if I can see the display refreshing

Video Card: Ati Radeon 9800 XXL , AMD Athlon 64 3000+ 

**Where can I find the relevant documentation for configuring the video card ? Tried /etc/x11/xorg.conf, but the system responded " /etc/x11/xorg.conf: No such file or directory"**

Thanks :-)

lspci listing:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge  (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890  South]
0000:00:06.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadca st Decoder (rev 01)
0000:00:07.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Pri sm Xbow] (rev 01)
0000:00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
0000:00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/ K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 98 00 XT]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)

Just for future reference, the path is /etc/X11/xorg.conf (your x was lower case, it thinks it is a different path)

---

### Post by bewire on 2006-10-15
> **igknighted said:**
> Just for future reference, the path is /etc/X11/xorg.conf (your x was lower case, it thinks it is a different path)

Thanks for noticing and sorry for the typo ...

bewire

---

