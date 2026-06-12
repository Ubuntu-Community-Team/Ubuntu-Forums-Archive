---
title: "Which would be better for my system?"
date: 2016-05-07
forum: General Help
---

### Post by BadassRare on 2016-05-07
```
computer                  
description: Mini Tower Computer
product: OptiPlex GX260
vendor: Winbond Electronics
serial: [REMOVED]
width: 32 bits
capabilities: smp-1.4 smp
configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=[REMOVED]
*-core
   description: Motherboard
   product: 02X378
   vendor: Winbond Electronics
   physical id: 0
   serial: [REMOVED]
 *-firmware
      description: BIOS
      vendor: Winbond Electronics
      physical id: 0
      version: A09
      date: 11/01/2004
      size: 64KiB
      capacity: 448KiB
      capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
 *-cpu
      description: CPU
      product: Intel(R) Pentium(R) 4 CPU 2.40GHz
      vendor: Intel Corp.
      physical id: 400
      bus info: cpu@0
      version: 15.2.7
      slot: Microprocessor
      size: 2400MHz
      capacity: 3060MHz
      width: 32 bits
      clock: 533MHz
      capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
      configuration: id=0
    *-cache:0
         description: L1 cache
         physical id: 700
         size: 8KiB
         capacity: 16KiB
         capabilities: internal write-back data
    *-cache:1
         description: L2 cache
         physical id: 701
         size: 512KiB
         capacity: 512KiB
         capabilities: internal varies unified
 *-memory
      description: System Memory
      physical id: 1000
      slot: System board or motherboard
      size: 1GiB
      capacity: 1GiB
    *-bank:0
         description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
         physical id: 0
         slot: DIMM_A
         size: 512MiB
         width: 64 bits
         clock: 266MHz (3.8ns)
    *-bank:1
         description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
         physical id: 1
         slot: DIMM_B
         size: 512MiB
         width: 64 bits
         clock: 266MHz (3.8ns)
 *-pci
      description: Host bridge
      product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
      vendor: Intel Corporation
      physical id: 100
      bus info: pci@0000:00:00.0
      version: 01
      width: 32 bits
      clock: 33MHz
      configuration: driver=agpgart-intel
      resources: irq:0 memory:f0000000-f7ffffff
    *-display
         description: VGA compatible controller
         product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
         vendor: Intel Corporation
         physical id: 2
         bus info: pci@0000:00:02.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm vga_controller bus_master cap_list rom
         configuration: driver=i915 latency=0
         resources: irq:16 memory:e8000000-efffffff memory:ff680000-ff6fffff
    *-usb:0
         description: USB controller
         product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
         vendor: Intel Corporation
         physical id: 1d
         bus info: pci@0000:00:1d.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: uhci bus_master
         configuration: driver=uhci_hcd latency=0
         resources: irq:16 ioport:ff80(size=32)
    *-usb:1
         description: USB controller
         product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
         vendor: Intel Corporation
         physical id: 1d.1
         bus info: pci@0000:00:1d.1
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: uhci bus_master
         configuration: driver=uhci_hcd latency=0
         resources: irq:19 ioport:ff60(size=32)
    *-usb:2
         description: USB controller
         product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
         vendor: Intel Corporation
         physical id: 1d.2
         bus info: pci@0000:00:1d.2
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: uhci bus_master
         configuration: driver=uhci_hcd latency=0
         resources: irq:18 ioport:ff40(size=32)
    *-usb:3
         description: USB controller
         product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
         vendor: Intel Corporation
         physical id: 1d.7
         bus info: pci@0000:00:1d.7
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm debug ehci bus_master cap_list
         configuration: driver=ehci-pci latency=0
         resources: irq:23 memory:ffa00800-ffa00bff
    *-pci
         description: PCI bridge
         product: 82801 PCI Bridge
         vendor: Intel Corporation
         physical id: 1e
         bus info: pci@0000:00:1e.0
         version: 81
         width: 32 bits
         clock: 33MHz
         capabilities: pci normal_decode bus_master
         resources: ioport:e000(size=4096) memory:ff800000-ff9fffff
       *-network:0
            description: Ethernet interface
            product: 3CR990-TX-97 [Typhoon 168-bit]
            vendor: 3Com Corporation
            physical id: 7
            bus info: pci@0000:01:07.0
            logical name: eth1
            version: 02
            serial: [REMOVED]
            size: 10Mbit/s
            capacity: 100Mbit/s
            width: 32 bits
            clock: 33MHz
            capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
            configuration: autonegotiation=on broadcast=yes driver=typhoon duplex=half firmware=03.001.008 latency=64 link=no maxlatency=5 mingnt=10 multicast=yes port=twisted pair speed=10Mbit/s
            resources: irq:16 ioport:ec80(size=128) memory:ff8c0000-ff8fffff
       *-network:1
            description: Ethernet interface
            product: 82540EM Gigabit Ethernet Controller
            vendor: Intel Corporation
            physical id: c
            bus info: pci@0000:01:0c.0
            logical name: eth0
            version: 02
            serial: [REMOVED]
            size: 100Mbit/s
            capacity: 1Gbit/s
            width: 32 bits
            clock: 66MHz
            capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
            configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=[REMOVED] latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
            resources: irq:18 memory:ff8a0000-ff8bffff ioport:ec40(size=64)
    *-isa
         description: ISA bridge
         product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
         vendor: Intel Corporation
         physical id: 1f
         bus info: pci@0000:00:1f.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: isa bus_master
         configuration: driver=lpc_ich latency=0
         resources: irq:0
    *-ide
         description: IDE interface
         product: 82801DB (ICH4) IDE Controller
         vendor: Intel Corporation
         physical id: 1f.1
         bus info: pci@0000:00:1f.1
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: ide bus_master
         configuration: driver=ata_piix latency=0
         resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:40000000-400003ff
    *-serial UNCLAIMED
         description: SMBus
         product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
         vendor: Intel Corporation
         physical id: 1f.3
         bus info: pci@0000:00:1f.3
         version: 01
         width: 32 bits
         clock: 33MHz
         configuration: latency=0
         resources: ioport:dc80(size=32)
    *-multimedia
         description: Multimedia audio controller
         product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
         vendor: Intel Corporation
         physical id: 1f.5
         bus info: pci@0000:00:1f.5
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list
         configuration: driver=snd_intel8x0 latency=0
         resources: irq:17 ioport:d800(size=256) ioport:dc40(size=64) memory:ffa00400-ffa005ff memory:ffa00000-ffa000ff
 *-scsi:0
      physical id: 1
      logical name: scsi0
      capabilities: emulated
    *-disk
         description: ATA Disk
         product: ST380023A
         vendor: Seagate
         physical id: 0.0.0
         bus info: scsi@0:0.0.0
         logical name: /dev/sda
         version: 3.33
         serial: [REMOVED]
         size: 74GiB (80GB)
         capabilities: partitioned partitioned:dos
         configuration: ansiversion=5 signature=000d1d7c
       *-volume:0
            description: EXT4 volume
            vendor: Linux
            physical id: 1
            bus info: scsi@0:0.0.0,1
            logical name: /dev/sda1
            logical name: /
            version: 1.0
            serial: [REMOVED]
            size: 73GiB
            capacity: 73GiB
            capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
            configuration: created=2016-03-03 07:03:37 filesystem=ext4 lastmountpoint=/ modified=2016-03-03 07:21:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-03-21 14:56:11 state=mounted
       *-volume:1
            description: Extended partition
            physical id: 2
            bus info: scsi@0:0.0.0,2
            logical name: /dev/sda2
            size: 1021MiB
            capacity: 1021MiB
            capabilities: primary extended partitioned partitioned:extended
          *-logicalvolume
               description: Linux swap / Solaris partition
               physical id: 5
               logical name: /dev/sda5
               capacity: 1021MiB
               capabilities: nofs
 *-scsi:1
      physical id: 2
      logical name: scsi1
      capabilities: emulated
    *-cdrom
         description: SCSI CD-ROM
         physical id: 0.0.0
         bus info: scsi@1:0.0.0
         logical name: /dev/cdrom
         logical name: /dev/sr0
         capabilities: audio
         configuration: status=nodisc
```
First off apologys on if i posted this in the incorrect spot. kinda newish to the forums and where to post things. I need some help on upgradeing my system to be able to keep up with the dependencys for cmake and things such as that. I am currently at 12.04 ubuntu (because upgradeing fully to 14.04 when it was newest lagged my system badly) I was wondering if possibly lubuntu or xubuntu or arch would be great for my system to keep it updated? I have no cash on me and probs won't for a little while, but anything would be greatly appricated

---

### Post by nerdtron on 2016-05-07
I think Xubuntu will still run fine on that machine. However if it still lags or too slow for you, try Lubuntu.

---

### Post by BadassRare on 2016-05-07
Thank you for the quick reply! I will try Xubuntu and see how it goes.

---

### Post by oldos2er on 2016-05-07
If you've only 1GB RAM I'd go with Lubuntu like nerdtron suggested.

---

