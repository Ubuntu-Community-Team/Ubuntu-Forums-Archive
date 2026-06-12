---
title: "Regular Image load problem"
date: 2007-12-19
forum: General Help
---

### Post by WildeBeest on 2007-12-19
The problem I have is when I do a normal (non-recovery) image boot, I get to where loading "periodic command scheduler crond" line is or some line after that, my PC reboots itself and sometimes just locks up.
I edited Grub to remove the quiet and slash options from the boot line.

But, if I select the recovery image and I can get to the root command line and type "telinit 3", Gusty works fine.

I'm new to Ubuntu and this is getting very frustrating.

---

### Post by danwood76 on 2007-12-19
when booting in recovery mode you end up in a root user session, it may be that something messed up in your /home dir or soemthing else thats messing with the normal user startup.

Have you done anything recently that would cause problems? (new drivers etc)

---

### Post by WildeBeest on 2007-12-19
This problem was from day one.

The live disk would reboot continuously too, and lockup occasionally.
I would never get to the menu that gives you the option to install it.

I had to do the alternate install in order to get the OS to install at all.

Thanks to the recovery image to be able to use Gusty at all. Everything works perfectly this way. I shouldn't have to get into the OS this way.

---

### Post by danwood76 on 2007-12-19
I would assume that you have some hardware issue.

Whats the spec of your system?

---

### Post by WildeBeest on 2007-12-19
I have XP Pro SP2 on the same machine, but on a differen drive(SATA). Dual boot configuration

Hardware specs
Abit AA8 Duramax motherboard
Pentium 4 D @ 3.0GHz
2GB A-Data Ram
400GB WD SATA HD(XP Pro)
300GB Maxtor IDE(Ubuntu 7.1)
Optiarc SATA DVD
NEC IDE DVD
Foxconn GE8400gs graphics card

XP Pro installed just fine.
I have the same problem with 7.04.

The lshw command provides the following output:

description: Computer
width: 32 bits
*-core
description: Motherboard
physical id: 0
*-memory
description: System memory
physical id: 0
size: 2027MB
*-cpu
product: Intel(R) Pentium(R) 4 CPU 3.00GHz
vendor: Intel Corp.
physical id: 1
bus info: cpu@0
version: 15.6.5
serial: 0000-0F65-0000-0000-0000-0000
size: 18EHz
width: 64 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc up pni monitor ds_cpl est tm2 cid cx16 xtpr lahf_lm
configuration: id=0
*-pci
description: Host bridge
product: 82925X/XE Memory Controller Hub
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 04
width: 32 bits
clock: 33MHz
*-pci:0
description: PCI bridge
product: 82925X/XE PCI Express Root Port
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master cap_list
configuration: driver=pcieport-driver
*-display
description: VGA compatible controller
product: GeForce 8400 GS
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: vga bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia
*-multimedia
description: Audio device
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 03
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel
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
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0 module=ehci_hcd
*-pci:1
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
product: RTL-8169 Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:02:01.0
logical name: eth0
version: 10
serial: 00:50:8d:e7:34:33
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
*-firewire
description: FireWire (IEEE 1394)
product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
vendor: Texas Instruments
physical id: 2
bus info: pci@0000:02:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: ohci bus_master cap_list
configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
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
*-cdrom
description: DVD writer
product: DVD_RW ND-3550A
vendor: _NEC
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/cdrom1
logical name: /dev/dvd1
logical name: /dev/scd0
logical name: /dev/sr0
version: 1.05
serial: [_NEC DVD_RW ND-3550A 1.0505093000
capabilities: removable audio cd-r cd-rw dvd dvd-r
configuration: ansiversion=5 status=open
*-ide:1
description: IDE interface
product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
version: 03
width: 32 bits
clock: 66MHz
capabilities: ide bus_master cap_list
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
willy@WES-Office-P4:~$ lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by WildeBeest on 2007-12-20
Bump to top
This is getting very frustrating that no one has any idea what's going on.

[SIZE="7"][COLOR="Red"]HELP![/COLOR][/SIZE]

---

### Post by danwood76 on 2007-12-20
Its probably your graphics card I would have thought.
You could try a different card or manually installing the display drivers from a text install.

That is the only weak link in your system in my opinion.

Its also possible that you have some messed up permissions in your install, you could try reinstalling from the alternative CD.

sorry I cant help further,
Danny

---

### Post by WildeBeest on 2007-12-20
If it is the graphics card, wouldn't the recovery image crash too?
It uses the same driver.

Does anyone know what the loads are after: "periodic command scheduler crond" up to the login screen.
Can anyone list them?

That should pin point the problem.

---

### Post by WildeBeest on 2007-12-22
Bump this back to the top.

Someone must have a clue what the problem is!

---

### Post by WildeBeest on 2007-12-26
Bump to top again.

[COLOR="Red"][SIZE="6"]ANYONE?[/SIZE][/COLOR]

---

### Post by danwood76 on 2007-12-27
is there anything in your Xorg.0.log or Xorg.0.log.old ?
if you boot normally then boot in recovery and run these in terminal:

cat /var/log/Xorg.0.log.old | grep '(EE)'
cat /var/log/Xorg.0.log.old | grep '(WW)'

and

cat /var/log/Xorg.0.log | grep '(EE)'
cat /var/log/Xorg.0.log | grep '(WW)'

and post the results, it may give some errors or warnings we can go on.

regards,
Danny

---

### Post by WildeBeest on 2007-12-27
cat /var/log/Xorg.0.log.old | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

cat /var/log/Xorg.0.log.old | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used



cat /var/log/Xorg.0.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

cat /var/log/Xorg.0.log | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used

---

