---
title: "problems booting"
date: 2008-03-09
forum: General Help
---

### Post by ADBD on 2008-03-09
Booting into ubuntu hangs for a few minutes and then I get this message:

BusyBox v.1.1.3(Debian 1,:1.1.1.3-5ebuntu7) Built-in shell(ash)
Enter 'help' for a list of built-in commands
(unitramfs)

I have to reboot 5-10 times before I can boot into ubuntu. The problem might be the 965 chipset or JMicron controller. Any commands I could try when booting?

lshw:
joni-desktop
description: Desktop Computer
product: OEM
vendor: OEM
version: OEM
serial: OEM
width: 32 bits
capabilities: smbios-2.2 dmi-2.2
configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-00508D945493
*-core
description: Motherboard
product: AB9/AB9RPO(Intel965+ICH
vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)
physical id: 0
version: 1.x (BIOS:15)
*-firmware
description: BIOS
vendor: Phoenix Technologies, LTD
physical id: 0
version: 6.00 PG (08/16/2007)
size: 128KB
capacity: 448KB
capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
*-cpu
description: CPU
product: Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz
vendor: Intel Corp.
physical id: 4
bus info: cpu@0
version: 6.15.6
serial: 0000-06F6-0000-0000-0000-0000
slot: Socket 775
size: 1904MHz
capacity: 4GHz
width: 64 bits
clock: 272MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
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
size: 2MB
capacity: 2MB
capabilities: synchronous external write-back
*-logicalcpu:0
description: Logical CPU
physical id: 0.1
width: 64 bits
capabilities: logical
*-logicalcpu:1
description: Logical CPU
physical id: 0.2
width: 64 bits
capabilities: logical
*-memory
description: System Memory
physical id: 1b
slot: System board or motherboard
size: 2GB
*-bank:0
description: DIMM Synchronous
physical id: 0
slot: C
size: 512MB
width: 64 bits
*-bank:1
description: DIMM Synchronous
physical id: 1
slot: C
size: 512MB
width: 64 bits
*-bank:2
description: DIMM Synchronous
physical id: 2
slot: C
size: 512MB
width: 64 bits
*-bank:3
description: DIMM Synchronous
physical id: 3
slot: C
size: 512MB
width: 64 bits
*-pci
description: Host bridge
product: 82P965/G965 Memory Controller Hub
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 02
width: 32 bits
clock: 33MHz
*-pci:0
description: PCI bridge
product: 82P965/G965 PCI Express Root Port
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
configuration: driver=pcieport-driver
*-display
description: VGA compatible controller
product: G71 [GeForce 7900 GS]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vga bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia
*-usb:0
description: USB Controller
product: 82801H (ICH8 Family) USB UHCI Contoller #4
vendor: Intel Corporation
physical id: 1a
bus info: pci@0000:00:1a.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:1
description: USB Controller
product: 82801H (ICH8 Family) USB UHCI Controller #5
vendor: Intel Corporation
physical id: 1a.1
bus info: pci@0000:00:1a.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:2
description: USB Controller
product: 82801H (ICH8 Family) USB2 EHCI Controller #2
vendor: Intel Corporation
physical id: 1a.7
bus info: pci@0000:00:1a.7
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0 module=ehci_hcd
*-multimedia
description: Audio device
product: 82801H (ICH8 Family) HD Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel
*-pci:1
description: PCI bridge
product: 82801H (ICH8 Family) PCI Express Port 1
vendor: Intel Corporation
physical id: 1c
bus info: pci@0000:00:1c.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
configuration: driver=pcieport-driver
*-pci:2
description: PCI bridge
product: 82801H (ICH8 Family) PCI Express Port 5
vendor: Intel Corporation
physical id: 1c.4
bus info: pci@0000:00:1c.4
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
configuration: driver=pcieport-driver
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 01
serial: 00:50:8d:94:54:93
size: 10MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=10MB/s
*-pci:3
description: PCI bridge
product: 82801H (ICH8 Family) PCI Express Port 6
vendor: Intel Corporation
physical id: 1c.5
bus info: pci@0000:00:1c.5
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
configuration: driver=pcieport-driver
*-storage
description: SATA controller
product: JMicron 20360/20363 AHCI Controller
vendor: JMicron Technologies, Inc.
physical id: 0
bus info: pci@0000:04:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
configuration: driver=ahci latency=0 module=ahci
*-ide
description: IDE interface
product: JMicron 20360/20363 AHCI Controller
vendor: JMicron Technologies, Inc.
physical id: 0.1
bus info: pci@0000:04:00.1
logical name: scsi6
version: 02
width: 32 bits
clock: 33MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=pata_jmicron latency=0 module=pata_jmicron
*-cdrom
description: DVD-RAM writer
product: DVDRW LH-18A1H
vendor: LITE-ON
physical id: 0.1.0
bus info: scsi@6:0.1.0
logical name: /dev/cdrom
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
version: HL07
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=open
*-usb:3
description: USB Controller
product: 82801H (ICH8 Family) USB UHCI Controller #1
vendor: Intel Corporation
physical id: 1d
bus info: pci@0000:00:1d.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:4
description: USB Controller
product: 82801H (ICH8 Family) USB UHCI Controller #2
vendor: Intel Corporation
physical id: 1d.1
bus info: pci@0000:00:1d.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:5
description: USB Controller
product: 82801H (ICH8 Family) USB UHCI Controller #3
vendor: Intel Corporation
physical id: 1d.2
bus info: pci@0000:00:1d.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:6
description: USB Controller
product: 82801H (ICH8 Family) USB2 EHCI Controller #1
vendor: Intel Corporation
physical id: 1d.7
bus info: pci@0000:00:1d.7
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0 module=ehci_hcd
*-pci:4
description: PCI bridge
product: 82801 PCI Bridge
vendor: Intel Corporation
physical id: 1e
bus info: pci@0000:00:1e.0
version: f2
width: 32 bits
clock: 33MHz
capabilities: pci subtractive_decode bus_master cap_list
*-firewire
description: FireWire (IEEE 1394)
product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
vendor: Texas Instruments
physical id: 2
bus info: pci@0000:05:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm ohci bus_master cap_list
configuration: driver=ohci1394 latency=68 maxlatency=4 mingnt=2 module=ohci1394
*-isa
description: ISA bridge
product: 82801HB/HR (ICH8/R) LPC Interface Controller
vendor: Intel Corporation
physical id: 1f
bus info: pci@0000:00:1f.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: isa bus_master cap_list
configuration: latency=0
*-ide:0
description: IDE interface
product: 82801H (ICH8 Family) 4 port SATA IDE Controller
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
logical name: scsi2
version: 02
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=ata_piix latency=0 module=ata_piix
*-disk
description: SCSI Disk
product: WDC WD2500KS-00M
vendor: ATA
physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sda
version: 02.0
serial: WD-WCANK6015908
size: 232GB
capabilities: partitioned partitioned:dos
configuration: ansiversion=5
*-volume:0
description: Linux filesystem partition
physical id: 1
bus info: scsi@2:0.0.0,1
logical name: /dev/sda1
capacity: 227GB
capabilities: primary bootable
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@2:0.0.0,2
logical name: /dev/sda2
size: 5930MB
capacity: 5930MB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 5930MB
capabilities: nofs
*-serial UNCLAIMED
description: SMBus
product: 82801H (ICH8 Family) SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 02
width: 32 bits
clock: 33MHz
configuration: latency=0
*-ide:1
description: IDE interface
product: 82801H (ICH8 Family) 2 port SATA IDE Controller
vendor: Intel Corporation
physical id: 1f.5
bus info: pci@0000:00:1f.5
version: 02
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list
configuration: driver=ata_piix latency=0 module=ata_piix

---

### Post by ADBD on 2008-03-09
anything?

---

### Post by Fixman on 2008-03-09
Does the "orange gauge" show, or the message happens before that? Could you boot before into Ubuntu?

---

### Post by ADBD on 2008-03-09
> **Fixman said:**
> Does the "orange gauge" show, or the message happens before that? Could you boot before into Ubuntu?

The orange gauge shows just a little (like a few millimeters) and it freezes there for a few minutes before taking me to that message. No, I've had this problem ever since I installed ubuntu a couple of days ago and I even did a re-install. After rebooting a few times it works and boots into ubuntu (but it's kinda annoying to boot 5-10 times before getting in :/)

---

### Post by ADBD on 2008-03-09
Also my graphics card is damaged from overclocking, getting artifacts and such. Could that cause problems like this?

---

### Post by ADBD on 2008-03-10
any boot parameters or something like that I can try to type in when booting?

---

### Post by ADBD on 2008-04-12
Am I really the only one with this problem? It's getting really annoying, I just had to reboot with ctrl+alt+del from the loading screen 20 times before ubuntu loaded. Usually it takes about 10 tries.

---

### Post by nelson2006 on 2008-04-12
[SIZE="2"]I've got booting problems also since yesterday. It gets to the orange gauge, freezes, and then tosses the following message:

*Starting ACPI services....
acpid: can't open socket /var/run/acpid.socket: Read only file system


Help, please :cry:!!![/SIZE]

---

### Post by ADBD on 2008-04-13
I wonder if this problem is caused by the same thing that causes the ubuntu live cd to not recognize my HDD most of the time (it almost never shows up in gparted on the live cd)?

---

