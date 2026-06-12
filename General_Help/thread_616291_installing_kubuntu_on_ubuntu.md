---
title: "installing kubuntu on ubuntu"
date: 2007-11-18
forum: General Help
---

### Post by zivxx on 2007-11-18
hey everyone...
ive burned the kubuntu CD and i want to install it...im already on ubuntu tho so when i enter the disc it asks me to open the pacakge manager and i don't see the kubuntu package...anyone know what to do?

---

### Post by Vince4Amy on 2007-11-18
Wouldn't of it have been easier just to install Kubuntu from the Repositories using:
 
```
sudo apt-get install kubuntu-desktop
```

---

### Post by derby007 on 2007-11-18
Now that you have the CD, you can do the following:
insert Kubuntu CD
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
logout | end session
When logging in choose 'Session Type' choose KDE, then login

---

### Post by zivxx on 2007-11-18
ok now when i have the kde, can i delete gnome?

---

### Post by zvacet on 2007-11-18
```
sudo aptitude remove ubuntu-desktop
```

---

### Post by derby007 on 2007-11-18
I wouldnt bother, TBH, you can use KDE as your default desktop enviornment & still have access to gnome applications. I dont think there is a great amount of 'disk saving' by removing Gnome. Hey, why not even give Xubuntu a go, same procedure.

---

### Post by zivxx on 2007-11-18
what does interface Xubuntu use?
i will gladly try all of them..but each download takes about 6 hours with my slow internet connection

---

### Post by knutschr on 2007-11-18
I use KDE as my default desktop.
I have also installed ubuntu-desktop and xubuntu-desktop.

At login I can choose which session to use.
Very good :-)

I did also install edubuntu-desktop.
There is, however, no option to start it.
Why?

---

### Post by derby007 on 2007-11-18
I presume it just installs the education software, eg. software for kids like  
Tuxpaint, Gcompriz, see: 
[http://www.edubuntu.org/UsingEdubuntu]("http://www.edubuntu.org/UsingEdubuntu")
Its could be installed by a net-admin & then run thin clients with it.

---

### Post by zivxx on 2007-11-18
is there any program build-in in linux for video recording things that going on the computer?so i can record the lags im talking about...after all maybe its normal

---

### Post by ramkumail on 2007-11-18
there is program called "gtk record my desktop". you can see more at [http://ubuntuforums.org/showthread.php?t=294605](http://ubuntuforums.org/showthread.php?t=294605)

---

### Post by derby007 on 2007-11-18
I'm not aware of any, either try gooooogling or start another thread in 'Multimedia' section might yield a better answer. What 'lags' are you seeing? do you mean a system-performance lag ? slowdown? do you need more RAM? etc.

Edit: ach, my submit was too late, someone has maybe answered your Q.......

---

### Post by zivxx on 2007-11-18
about the video they did...but you can go to [http://ubuntuforums.org/showthread.php?t=614648](http://ubuntuforums.org/showthread.php?t=614648)
and see my entire post about my lags..maybe your'e the one that will have the answers after 2 days

---

### Post by derby007 on 2007-11-18
What is your system ? Computer type DELL/HP etc, Processor (speed, dual-core), Harddrive, RAM, graphics > card or onboard, other attached hardware > USB drive, printer, networking etc.

---

### Post by zivxx on 2007-11-18
DELL intel pentium 4...i really don't remember the rest about processor 80gb 1gb ram ddr2 graphic is avi X series..im not sure about that too heeehee :|

---

### Post by knutschr on 2007-11-18
```

sudo lshw

```

---

### Post by zivxx on 2007-11-18
ok...i did it but didn't knew exactly what to copy so here goes:
description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8I915P Duo
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F6 (01/21/2005)
          size: 128KB
          capacity: 320KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 4GHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM 66 MHz (15.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GB
             width: 64 bits
             clock: 66MHz (15.2ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV370 [Radeon X300SE]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5789 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 11
                serial: 00:0f:ea:f9:fb:4e
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5789-v3.29a ip=192.168.123.130 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: Ethernet 100/10 MBit
                vendor: Davicom Semiconductor, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 31
                serial: 00:01:53:81:94:f7
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=64 link=no maxlatency=40 mingnt=20 module=dmfe multicast=yes
           *-storage
                description: RAID bus controller
                product: VT6410 ATA133 RAID controller
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@0000:04:06.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=VIA_IDE latency=32 module=via82cxxx
              *-ide
                   description: IDE Channel 0
                   physical id: 0
                   bus info: ide@0
                   logical name: ide0
                   clock: 33MHz
                 *-cdrom:0
                      description: DVD-RAM writer
                      product: HL-DT-ST DVDRAM GSA-4163B
                      physical id: 0
                      bus info: ide@0.0
                      logical name: /dev/hda
                      version: A103
                      serial: K0C53NB3646
                      capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                      configuration: mode=udma2 status=nodisc
                 *-cdrom:1
                      description: DVD reader
                      product: HL-DT-STDVD-ROM GDR8163B
                      physical id: 1
                      bus info: ide@0.1
                      logical name: /dev/hdb
                      version: 0L23
                      capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd
                      configuration: mode=udma2 status=nodisc
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: SAMSUNG SP0802N
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TK30
                serial: S00JJ40Y519653
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 73GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1466MB
                   capacity: 1466MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1466MB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

---

### Post by derby007 on 2007-11-18
I wonder what driver you have for the ATI graphics: RV370 5B60 [Radeon X300 (PCIE)]
Pls post what you get for : 'cat /etc/X11/xorg.conf'

---

### Post by zivxx on 2007-11-18
here it is:
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

---

### Post by derby007 on 2007-11-18
Try this: this may or may not do anything: worth a try I reckon:

sudo gedit /etc/X11/xorg.conf

#add this to it (after the files section)>>>>

Section "Module"
#	Load		"fglrx"
	Load		"dbe"
	Load		"extmod"
	Load		"fbdevhw"
	Load		"glx"
	Load		"record"
	Load		"freetype"
	Load		"type1"
	Load		"dri"
EndSection

>> then 'save', exit Gedit, then reboot......  fingers crossed!

---

### Post by zivxx on 2007-11-18
ok i did it...it didn't worked but   im not sure i did it right tho, it look like that now:
# xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
Section "Module"
 # Load "fglrx"
 Load "dbe"
 Load "extmod"
 Load "fbdevhw"
 Load "glx"
 Load "record"
 Load "freetype"
 Load "type1"
 Load "dri"
 EndSection

is it good?

---

### Post by zivxx on 2007-11-18
second edit:
im going away for 4 hours now, please everyone that can help post you suggestions i will check them later

---

### Post by derby007 on 2007-11-18
Its usually at the top: after Section "Files", but maybe it doesnt matter. 

 I'm still guessing its you graphics driver........If you rebooted & it hasn't improved your situation, then you'll just have to keep trying, and maybe do a little reading up on Linux, hardware, Ubuntu etc. ie. get a feel for it ! There's loads of help available. 
Q. Do you know if you made any modifications to Ubuntu after you installed it? ie. did u download any software, updates, install hardware?

If you have Gutsy installed, go to the 'restricted drivers' tab on your 'menu', in System &#8594; Administration &#8594; Restricted Devices Manager, choose this option. 

If it asks for FGLXR then install the 'xorg-driver-fglrx', by doing: apt-get install xorg-driver-fglrx.

Then do : apt-get install xserver-xgl

Then reboot..........

Edit: I'm off until Thursday, so good luck with it....... :)

---

### Post by zivxx on 2007-11-18
erm....i don't really know what you mean..so there was something disabled there so i enbaled it and its just made everything really small and i keep lagging...can anyone else explain to me what he meant?

---

