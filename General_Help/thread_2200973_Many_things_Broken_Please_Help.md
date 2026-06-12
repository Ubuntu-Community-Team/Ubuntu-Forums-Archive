---
title: "Many things Broken Please Help"
date: 2014-01-22
forum: General Help
---

### Post by curtis6 on 2014-01-22
Okay, So today I loaded up my Windows 7 so I could play a game(never really got around to that), and I noticed how Cool my laptop was running on idle compared to linux. I got to searching google on how to cool my ubuntu down...one thing lead to another and I uninstalled the fglrx drivers and deleted my /etc/X11/xorg.conf. Granted it is running cooler, but it Broke compiz, my touchpad is jittery when i use it, and I can't Tap-to-click on the pad.
By Compiz being broken I mean that It doesn't snap to sides, Pull to side to resize it to half screen doesn't work, SFX don't work, ect. When i compiz --replace It starts up, but its very spazy and doesn't function well at all.
I run Ubuntu 12.04 with Gnome Classic Desktop. My GPU is an "ATI Mobility Radeon 5700". Any help on how to fix these problems is much appreciate

---

### Post by QIII on 2014-01-22
Hi!

Could you give us the full system specs on your machine?  In particular, does it have hybrid Intel/ATI graphics?

Thanks.

---

### Post by curtis6 on 2014-01-22
I don't believe It is. Its an M15x Alienware
```
curtis-m15x                   description: Portable Computer
    product: M15x ()
    vendor: Alienware
    version: A08
    serial: 75K63P1
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=portable cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=44454C4C-3500-104B-8036-37C04F335031
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Alienware
          physical id: 1
          version: A08
          date: 08/24/2010
          size: 118KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-board UNCLAIMED
          description: Motherboard
          vendor: Alienware
          physical id: 3
          version: A08
          serial: .75K63P1.              .
          slot: Not Applicable
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          slot: CPU 1
          size: 931MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 id=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: burst internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: L3 Cache
             size: 3MiB
             capacity: 8MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 4.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 4.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 4.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 4.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 4.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 4.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 4.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 4.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 4.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 4.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 4.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 4.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 4.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 4.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 4.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 4.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: KF073F-ELD
             vendor: AMD
             physical id: 0
             serial: 66203BEB
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: KF073F-ELD
             vendor: AMD
             physical id: 1
             serial: 66203AEB
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu:1
          physical id: 0
          bus info: cpu@1
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          size: 931MHz
          capacity: 931MHz
          capabilities: vmx ht cpufreq
          configuration: id=4
        *-logicalcpu:0
             description: Logical CPU
             physical id: 4.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 4.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 4.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 4.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 4.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 4.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 4.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 4.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 4.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 4.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 4.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 4.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 4.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 4.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 4.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 4.10
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 18
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:cfe00000-cfefffff ioport:d0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Madison [Mobility Radeon HD 5730 / 6570M]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:d0000000-dfffffff memory:cfee0000-cfefffff ioport:2000(size=256) memory:cfe00000-cfe1ffff
           *-multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5000 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:44 memory:cfedc000-cfedffff
        *-network
             description: Ethernet interface
             product: 82577LC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 06
             serial: 84:2b:2b:83:48:b5
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.10-6 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:41 memory:f0f00000-f0f1ffff memory:f0f24000-f0f24fff ioport:1800(size=32)
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f0f27000-f0f273ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f0f20000-f0f23fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:f0600000-f07fffff ioport:f0000000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:4000(size=4096) memory:f0800000-f09fffff ioport:f0200000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:5000(size=4096) memory:f0a00000-f0bfffff ioport:f0400000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM43224 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: c0:cb:38:92:b5:ac
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.16 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:19 memory:f0a00000-f0a03fff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0f27400-f0f277ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f0c00000-f0cfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 7
                bus info: pci@0000:09:07.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:16 memory:f0c00000-f0c007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 7.1
                bus info: pci@0000:09:07.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:17 memory:f0c00800-f0c008ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 7.2
                bus info: pci@0000:09:07.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r592 latency=32
                resources: irq:17 memory:f0c01000-f0c010ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 7.3
                bus info: pci@0000:09:07.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=32
                resources: irq:17 memory:f0c01400-f0c014ff
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:1850(size=8) ioport:1844(size=4) ioport:1848(size=8) ioport:1840(size=4) ioport:1820(size=32) memory:f0f26000-f0f267ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f0f27800-f0f278ff ioport:1860(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:f0f25000-f0f25fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9500420AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: D005
             serial: 5VJAHWP7
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=9d413413
           *-volume:0
                description: Windows FAT volume
                vendor: Winbond Electronics
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT16
                serial: 3030-3030
                size: 39MiB
                capacity: 39MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=DellUtility
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 438GiB
                capacity: 438GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 14GiB
              *-logicalvolume:1
                   description: HPFS/NTFS partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 49GiB
              *-logicalvolume:2
                   description: Linux swap / Solaris partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 8GiB
                   capabilities: nofs
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 16GiB
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   logical name: /
                   capacity: 348GiB
                   configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=remount-ro,user_xattr state=mounted
     *-scsi:1
          physical id: 4
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW DC-8A2SH
             vendor: PLDS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 3D12
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0.0V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: outbound
  *-power UNCLAIMED
       description: To Be Defined By O.E.M
       product: To Be Defined By O.E.M
       vendor: To Be Defined By O.E.M
       physical id: 3
       version: 2.50
       serial: To Be Defined By O.E.M
       capacity: 32768mWh

```

---

### Post by curtis6 on 2014-01-22
I have Compiz working correctly again(As far as I can tell). I used [http://www.backtrack-linux.org/forums/archive/index.php/t-48904.html](http://www.backtrack-linux.org/forums/archive/index.php/t-48904.html) to enable the i915 module. And computer is running 20 degrees cooler W/ load. But my touchpads curser is still shaking and I still can't Tap-to-click

---

### Post by curtis6 on 2014-01-23
Bumb. How do I fix shakey mouse

---

