---
title: "Screen resolution wrong after latest 12.04 update"
date: 2013-01-18
forum: General Help
---

### Post by Bruce Kaufman on 2013-01-18
I just installed an update for 12.04, which required a reboot. After the reboot, the screen resolution is wrong (screen is stretched). The Monitor utility says my screen is LAPTOP (it's not) and the "detect Monitor" button does not do anything. 

Also tried changing resolution using grub-customizer but it doesn't seem to help either. In fact now on boot I get "error: no video mode activated" 

Also unplugged monitor.

Suggestions?

Thanks,

---

### Post by ManamiVixen on 2013-01-18
Care to describe what hardware you have? Memory, CPU, Graphics, ect.... :-k

---

### Post by Bruce Kaufman on 2013-01-18
description: Desktop Computer
    product: TH67+ (None)
    vendor: BIOSTAR Group
    version: 6.0
    serial: None
    width: 32 bits
    capabilities: smbios-2.7 dmi-2.7 smp-1.4 smp
    configuration: chassis=desktop cpus=4 family=None sku=None uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: TH67+
       vendor: BIOSTAR Group
       physical id: 0
       version: 6.0
       serial: None
       slot: None
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4.6.4
          date: 02/17/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cache:0
          description: L1 cache
          physical id: 4
          size: 256KiB
          capacity: 256KiB
          capabilities: internal varies
     *-cache:1
          description: L2 cache
          physical id: 5
          size: 1MiB
          capacity: 1MiB
          capabilities: internal varies unified
     *-cache:2
          description: L3 cache
          physical id: 6
          size: 6MiB
          capacity: 6MiB
          capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBRL
             vendor: Undefined
             physical id: 0
             serial: 00000000
             slot: A1_DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBRL
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: A1_DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBRL
             vendor: Undefined
             physical id: 2
             serial: 00000000
             slot: A1_DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBRL
             vendor: Undefined
             physical id: 3
             serial: 00000000
             slot: A1_DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i5-2300 CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 15
          bus info: cpu@0
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          slot: SOCKET 0
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 id=2 threads=4
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             width: 64 bits
             capabilities: logical
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: vmx ht cpufreq
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             capabilities: logical
     *-cpu:2
          physical id: 2
          bus info: cpu@2
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: vmx ht cpufreq
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             capabilities: logical
     *-cpu:3
          physical id: 3
          bus info: cpu@3
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: vmx ht cpufreq
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:50 memory:fb308000-fb30800f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:fb307000-fb3073ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:51 memory:fb300000-fb303fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) ioport:d2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 06
                serial: 00:30:67:c2:f1:e4
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.14 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:49 ioport:e000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fb200000-fb2fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fb200000-fb201fff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
             resources: memory:fb100000-fb1fffff
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
                resources: memory:fb100000-fb1fffff
              *-network UNCLAIMED
                   description: Network controller
                   product: ACX 111 54Mbps Wireless Interface
                   vendor: Texas Instruments
                   physical id: 0
                   bus info: pci@0000:04:00.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: latency=32
                   resources: memory:fb120000-fb121fff memory:fb100000-fb11ffff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:fa000000-fb0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:d000(size=128) memory:fb000000-fb07ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:fb080000-fb083fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fb306000-fb3063ff
        *-isa
             description: ISA bridge
             product: H67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:fb305000-fb3057ff
           *-disk:0
                description: ATA Disk
                product: MAXTOR STM350063
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9QG3VT44
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000efced
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4efabdac-588e-4ae3-b0f1-785893717bb7
                   size: 449GiB
                   capacity: 449GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-03-19 19:56:30 filesystem=ext4 lastmountpoint=/ modified=2012-10-09 17:40:56 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-10-13 21:49:23 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 15GiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST3300620AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 5QF3LQR1
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2c6abd30
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/backup
                   version: 1.0
                   serial: 47f51ee4-136e-464a-8a49-3abbe2209500
                   size: 279GiB
                   capacity: 279GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2012-03-15 12:20:30 filesystem=ext3 modified=2012-10-13 21:49:27 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,barrier=1,data=ordered mounted=2012-10-13 21:49:27 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: iHAS324   B
                vendor: ATAPI
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/sr0
                version: AL14
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:2
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 3
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: 05.0
                serial: WD-WCAW32266001
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1ea0e370
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: f2fc5cf0-5f8c-43b1-85ef-a1b3a2912cc2
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-10-12 08:47:54 filesystem=ext4 lastmountpoint=/media/wd-1tb modified=2012-10-12 12:01:50 mounted=2012-10-12 11:38:23 state=clean
           *-disk:3
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sdd
                version: 05.0
                serial: WD-WCATR9940047
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6d832d8b
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sdd1
                   version: 1.0
                   serial: 493eed01-729b-4513-817a-d12a1ddd1f8c
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-10-12 11:44:59 filesystem=ext4 modified=2012-10-12 11:45:06 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fb304000-fb3040ff ioport:f000(size=32)

LG LCD 'Flatron' display - made in 2010

---

### Post by ManamiVixen on 2013-01-18
try this.
[B]sudo apt-get remove --purge nvidia-current
sudo apt-get autoremove
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
[/B]**sudo apt-get install nvidia-current nvidia-settings**

---

### Post by Bruce Kaufman on 2013-01-19
Thanks. That did the trick!

---

