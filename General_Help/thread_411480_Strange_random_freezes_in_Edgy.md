---
title: "Strange random freezes in Edgy"
date: 2007-04-16
forum: General Help
---

### Post by danielm on 2007-04-16
Hi,

I just put together a new box a few days ago, and installed Edgy. I am experiencing some odd, random system freezes while using it (by freeze I mean the mouse cursor no longer moves, no response to keyboard and I can't even SSH in, so it's completely hosed so I have to hold down my power button to kill it - the machine does not freeze if I am not using it). My first suspicion was that my CPU was overheating, so by applying new paste and tightening the heatsink, i was able to reduce the temperature by 20C (from 60-70C before). However, the crashes continued. I suspected the video card, since it is an Nvidia GeForce 7600GT (by XFX) and have read that it has caused others problems in the past. So far, I have been trying to cause the OS to lock up with bzflag, but to no avail. I have, however noticed these lock ups occur when using either firefox (usually happened when using this app), locking, unlocking and then locking the desktop (xscreensaver), and while changing themes a few times in gnome-theme-manager. This makes me suspicious of whether Gnome-related apps are to blame. 

Has anyone experienced this kind of behavior with Edgy? Any ideas for what may be the cause?


My xorg.conf if provided below just in case. Please ask me any questions you may have about my hardware if you suspect it may be the cause, or any log files that would help.


********************************************************** xorg.conf **********************************************************************************
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
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
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pl"
        Option          "XkbOptions"    "lv3:ralt_switch"
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
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "TwinView" "True"
        Option          "TwinViewOrientation" "RightOf"
        Option          "UseEdidFreqs" "True"
        Option          "MetaModes" "1600x1200,1600x1200;"
        Option          "UseDisplayDevice" "DFP"
        Option          "ConnectedMonitor" "DFP, DFP"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1
024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1
024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1
024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624
" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624
" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624
" "800x600" "720x400" "640x480"
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

Section "Extensions"
        Option "Composite" "Disable"
EndSection

---

### Post by Spectre5 on 2007-04-17
I get these random freezes too...any have any ideas?  Mine even happen when I am not using the computer (i.e. I leave it on, turn off the monitor, then come back and turn the monitor on to find my frozen screen underneath).

These happen randomly for me and I am using xubuntu 6.10.  The only way I have been able to replicate these reliably is via Scite...load a .c file, click compile, then try to resize the scite window = freeze.  It freezes as soon as I click the resize corner thing....I was unable to get useful help regarding this at the scite bug reporting site.  Although it may be a scite problem, I also get the same freezes when not using scite....randomly.

When it happens, nothing responds...nothing is responsive besides killing the power.

Any ideas?

Here is my lspci:

00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
Subsystem: Compaq Computer Corporation Unknown device b165
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 3
Memory at 44000000 (32-bit, prefetchable) [size=64M]
Memory at 40100000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
I/O behind bridge: 00001000-00001fff
Memory behind bridge: 40000000-400fffff
Prefetchable memory behind bridge: 20000000-200fffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
Subsystem: Intel Corporation 82801AA IDE
Flags: bus master, medium devsel, latency 0
I/O ports at 2020 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
Subsystem: Intel Corporation 82801AA USB
Flags: bus master, medium devsel, latency 0, IRQ 11
I/O ports at eec0 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
Subsystem: Intel Corporation 82801AA SMBus
Flags: medium devsel, IRQ 5
I/O ports at eee0 [size=16]

01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
Subsystem: Compaq Computer Corporation Unknown device b19d
Flags: bus master, medium devsel, latency 64, IRQ 5
I/O ports at 1000 [size=256]
Capabilities: <access denied>

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 3
I/O ports at 1400 [size=256]
Memory at 40000000 (32-bit, non-prefetchable) [size=256]
[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
Capabilities: <access denied>

01:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 01 [Hayes/16450])
Subsystem: PCTel Inc Unknown device 0001
Flags: medium devsel, IRQ 11
I/O ports at 1800 [size=64]
Capabilities: <access denied>

---

### Post by danielm on 2007-04-17
I have gotten it to freeze without intervention just after posting above. The screensaver kicked in and locked my box, and then apparently froze. I will also provide my lspci output, shown below.

00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation SATA Controller 1 IDE (rev 02)
00:1f.3 SMBus: Intel Corporation SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation SATA Controller 2 IDE (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0391 (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
07:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by danielm on 2007-04-17
Also, I have an Intel 2 Core Duo. Someone I spoke with mentioned that the kernel needs to be recompiled it to work?? Is that true? Currently, I see both processors. If this is necessary, what would I need to recompile with?

---

### Post by danielm on 2007-04-17
Also, I have an Intel 2 Core Duo. Someone I spoke with mentioned that the kernel needs to be recompiled for it to work?? Is that true? Currently, I see both processors. If this is necessary, what would I need to recompile with?

---

### Post by danielm on 2007-04-19
interesting problem, which has been reported by several people, but not that i am aware is fixed (i wonder if it is related to the freezes i experience above). when i boot the feisty install CD, and select install (or anything that boots ubuntu), i get something like the following message after the BusyBox "banner":

/bin/sh: can't access tty; job control turned off
(initramfs) [     107.276423] ata6.00: failed to set xfermode (err_mask=0x4)
[     137.922875] ata6.00: failed to set xfermode (err_mask=0x40)
[     173.065563] ata6.00: failed to set xfermode (err_mask=0x40)
[     208.212207] ata6.00: failed to set xfermode (err_mask=0x40)

I've noticed some launchpad and mail archive posts, but nothing definite about a fix or anything. apparently this has been a problem for at least  4 months. 

Anyone actually fix this? Hopefully in a sane way that won't result in an install that breaks everything in the future?

---

### Post by danielm on 2007-04-19
also, i have heard, but i am uncertain, that intel e6600 processors have been tied to random freezes which i was experiencing in edgy. of course, i'm more concerned with getting feisty working at the moment, because hopefully some of this stuff has been fixed.

i should also add that i do not have a lite-on cd-rw drive (i have a samsung SH-S183L LS SATA ) but i previously had an ide cdrw drive and dvd drive. same error in both.

---

### Post by dagrump on 2007-04-19
My machine running edgy freezes up while using firefox, mainly during page refreshes, switching to another tab. I figured it was just firefox didn't seem to like my hardware. I was considering upgrading to feisty to see if the issue remains, it is totally random, might not happen for days, then it'll freeze 2 or 3 times in less than an hour.  If any one figures something out I'd be interested as too the cause, so if I run into it again I'd have a starting point. It is nice to know it's not just me.

---

### Post by danielm on 2007-04-19
Found and posted to these pages about feisty. under edgy, i don't get the pci error after disabling the jmicron controller in bios. but i sitll have yet to see if that fixes the freezing. 

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

---

### Post by danielm on 2007-04-19
freezing still happens with edgy :).

my hopes lie with feisty...

---

### Post by justinlindh on 2007-04-20
I get random lockups, also. I'm running on AMD64 3000+ (32-bit Feisty) with ATi 9800Pro. I have noticed that if I boot off of an older kernel (2.6.<something>.10) that the freezes go away. Whenever I boot off of the newer kernels, my PC will freeze up seemingly randomly. I've even reproduced this by just sitting at the login screen in X. I've experienced this same problem on another computer using the Live CD (it's an AMD64 3200+, Gigabyte K8GNSX-P or similar).

These lockups make the OS unusable, which is a serious shame. My plan is to use the older kernel and continue to try new kernel releases to see if they alleviate the problem.

---

### Post by Spectre5 on 2007-04-22
Changing default depth in xorg.conf from 24 to 16 may have fixed the issue for me....at least Scite does not freeze up  every time I compile as I mentioned before....hopefully I will get no  freezes now   :)

-Scott

---

### Post by ness0216 on 2007-04-23
I'm having the same issues. My setup worked fine for a day and now I get random freezes where nothing is responsive except doing a hard reboot. I was thinking it was because I have my root file system installed on a SATA RAID 0 array. I'm going to try installing dapper this afternoon instead of edgy and see if I get a stable system. Also I'm going to disable hardware raid and go the software route.

---

### Post by danielm on 2007-05-02
So I tried moving to Feisty (which I suggest you all to try; perhaps it'll fix the problem for you, or you'll get an error message that will be more informative). With feisty the situation is worse (or better if error messages are informative). I cannot even boot the installation properly. It looks like it's a JMicron JMB363 issue in my case. Here are some bugs on launchpad about this, some of which I've also posted to:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89380](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89380)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64574](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/64574)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)

I have not found any fixes yet.

---

