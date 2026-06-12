---
title: "Ubuntu 16.04 does not detect all RAM banks"
date: 2017-01-20
forum: General Help
---

### Post by jm33 on 2017-01-20
I have just got a new computer with 32 GB RAM (4 DIMMS of 8 GB) and an i7 processor.
I installed a fresh installation of ubuntu Xenial, but the system does not recognise all the memory banks (only 16 GB, 2 banks).
I have already tried upgrading the kernel (to 4.8.1) but still no change.
The BIOS (UEFI) shows all memory banks, and the full 32 GB, but Ubuntu cannot find it.

   The result of running sudo lshw is below.

What puzzles me the most is that it shows RAM banks 1 and 3 as empty (relevant lines copied below), when in reality there are SODIMMS just like the other two in them

   ```
*-memory
           description: System Memory
           physical id: 13
           slot: System board or motherboard
           size: 16GiB

         *-bank:0

              description: DIMM Synchronous 2133 MHz (0.5 ns)

              product: CMK16GX4M2A2400C14

              vendor: AMI

              physical id: 0

              serial: 00000000

              slot: ChannelA-DIMM0

              size: 8GiB

              width: 64 bits
              clock: 2133MHz (0.5ns)
 [COLOR=#ff0000]        *-bank:1
[/COLOR]
[COLOR=#ff0000]             description: DIMM [empty][/COLOR]
[COLOR=#ff0000]             physical id: 1[/COLOR]

[COLOR=#ff0000]             slot: ChannelA-DIMM1[/COLOR]
         *-bank:2
              description: DIMM Synchronous 2133 MHz (0.5 ns)
              product: CMK16GX4M2A2400C14
              vendor: AMI
              physical id: 2
              serial: 00000000
              slot: ChannelB-DIMM0
              size: 8GiB
              width: 64 bits
              clock: 2133MHz (0.5ns)
 [COLOR=#ff0000]        *-bank:3
[/COLOR]
[COLOR=#ff0000]             description: DIMM [empty][/COLOR]

[COLOR=#ff0000]             physical id: 3[/COLOR]
[COLOR=#ff0000]             slot: ChannelB-DIMM1[/COLOR]




Any help/pointers would be highly appreciated

sudo lshw output:

     description: Desktop Computer
     product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
     vendor: To Be Filled By O.E.M.
     version: To Be Filled By O.E.M.
     serial: To Be Filled By O.E.M.
     width: 64 bits
     capabilities: smbios-2.8 dmi-2.8 vsyscall32
     configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
   *-core
        description: Motherboard
        product: Z170 Extreme4
        vendor: ASRock
        physical id: 0
        serial: M80-67017701762
      *-firmware
           description: BIOS
           vendor: American Megatrends Inc.
           physical id: 0
           version: P7.00
           date: 09/09/2016
           size: 64KiB
           capacity: 13MiB
           capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
      *-cache:0
           description: L1 cache
           physical id: e
           slot: L1 Cache
           size: 128KiB
           capacity: 128KiB
           capabilities: synchronous internal write-back data
           configuration: level=1
      *-cache:1
           description: L1 cache
           physical id: f
           slot: L1 Cache
           size: 128KiB
           capacity: 128KiB
           capabilities: synchronous internal write-back instruction
           configuration: level=1
      *-cache:2
           description: L2 cache
           physical id: 10
           slot: L2 Cache
           size: 1MiB
           capacity: 1MiB
           capabilities: synchronous internal write-back unified
           configuration: level=2
      *-cache:3
           description: L3 cache
           physical id: 11
           slot: L3 Cache
           size: 8MiB
           capacity: 8MiB
           capabilities: synchronous internal write-back unified
           configuration: level=3
      *-cpu
           description: CPU
           product: Intel(R) Core(TM) i7-7700 CPU @ 3.60GHz
           vendor: Intel Corp.
           physical id: 12
           bus info: cpu@0
           version: Intel(R) Core(TM) i7-7700 CPU @ 3.60GHz
           serial: To Be Filled By O.E.M.
           slot: CPUSocket
           size: 1165MHz
           capacity: 4200MHz
           width: 64 bits
           clock: 100MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
           configuration: cores=4 enabledcores=4 threads=8
      *-memory
           description: System Memory
           physical id: 13
           slot: System board or motherboard
           size: 16GiB
         *-bank:0
              description: DIMM Synchronous 2133 MHz (0.5 ns)
              product: CMK16GX4M2A2400C14
              vendor: AMI
              physical id: 0
              serial: 00000000
              slot: ChannelA-DIMM0
              size: 8GiB
              width: 64 bits
              clock: 2133MHz (0.5ns)
         *-bank:1
              description: DIMM [empty]
              physical id: 1
              slot: ChannelA-DIMM1
         *-bank:2
              description: DIMM Synchronous 2133 MHz (0.5 ns)
              product: CMK16GX4M2A2400C14
              vendor: AMI
              physical id: 2
              serial: 00000000
              slot: ChannelB-DIMM0
              size: 8GiB
              width: 64 bits
              clock: 2133MHz (0.5ns)
         *-bank:3
              description: DIMM [empty]
              physical id: 3
              slot: ChannelB-DIMM1
      *-pci
           description: Host bridge
           product: Intel Corporation
           vendor: Intel Corporation
           physical id: 100
           bus info: pci@0000:00:00.0
           version: 05
           width: 32 bits
           clock: 33MHz
         *-display
              description: VGA compatible controller
              product: Intel Corporation
              vendor: Intel Corporation
              physical id: 2
              bus info: pci@0000:00:02.0
              version: 04
              width: 64 bits
              clock: 33MHz
              capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
              configuration: driver=i915 latency=0
              resources: irq:138 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
         *-usb
              description: USB controller
              product: Sunrise Point-H USB 3.0 xHCI Controller
              vendor: Intel Corporation
              physical id: 14
              bus info: pci@0000:00:14.0
              version: 31
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi xhci bus_master cap_list
              configuration: driver=xhci_hcd latency=0
              resources: irq:127 memory:df130000-df13ffff
            *-usbhost:0
                 product: xHCI Host Controller
                 vendor: Linux 4.8.1-040801-generic xhci-hcd
                 physical id: 0
                 bus info: usb@1
                 logical name: usb1
                 version: 4.08
                 capabilities: usb-2.00
                 configuration: driver=hub slots=16 speed=480Mbit/s
               *-usb:0
                    description: Generic USB device
                    product: 802.11 n WLAN
                    vendor: TPlink
                    physical id: 3
                    bus info: usb@1:3
                    version: 1.01
                    serial: 1.0
                    capabilities: usb-2.00
                    configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
               *-usb:1
                    description: Mouse
                    product: USB Optical Mouse
                    vendor: Logitech
                    physical id: 8
                    bus info: usb@1:8
                    version: 67.00
                    capabilities: usb-2.00
                    configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
               *-usb:2
                    description: Video
                    product: QuickCam E 3500
                    vendor: Logitech, Inc.
                    physical id: 9
                    bus info: usb@1:9
                    version: 0.06
                    serial: 3F43DB20
                    capabilities: usb-2.00
                    configuration: driver=snd-usb-audio maxpower=500mA speed=480Mbit/s
               *-usb:3
                    description: Mass storage device
                    product: Mass Storage Device
                    vendor: Generic
                    physical id: c
                    bus info: usb@1:c
                    version: 1.29
                    serial: 058F312D81B
                    capabilities: usb-2.00 scsi
                    configuration: driver=usb-storage maxpower=250mA speed=480Mbit/s
               *-usb:4
                    description: Keyboard
                    product: Dell USB Keyboard
                    vendor: Dell
                    physical id: e
                    bus info: usb@1:e
                    version: 3.01
                    capabilities: usb-1.10
                    configuration: driver=usbhid maxpower=70mA speed=2Mbit/s
            *-usbhost:1
                 product: xHCI Host Controller
                 vendor: Linux 4.8.1-040801-generic xhci-hcd
                 physical id: 1
                 bus info: usb@2
                 logical name: usb2
                 version: 4.08
                 capabilities: usb-3.00
                 configuration: driver=hub slots=10 speed=5000Mbit/s
         *-generic UNCLAIMED
              description: Signal processing controller
              product: Sunrise Point-H Thermal subsystem
              vendor: Intel Corporation
              physical id: 14.2
              bus info: pci@0000:00:14.2
              version: 31
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi bus_master cap_list
              configuration: latency=0
              resources: memory:df14e000-df14efff
         *-communication
              description: Communication controller
              product: Sunrise Point-H CSME HECI #1
              vendor: Intel Corporation
              physical id: 16
              bus info: pci@0000:00:16.0
              version: 31
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi bus_master cap_list
              configuration: driver=mei_me latency=0
              resources: irq:139 memory:df14d000-df14dfff
         *-storage
              description: SATA controller
              product: Sunrise Point-H SATA controller [AHCI mode]
              vendor: Intel Corporation
              physical id: 17
              bus info: pci@0000:00:17.0
              version: 31
              width: 32 bits
              clock: 66MHz
              capabilities: storage msi pm ahci_1.0 bus_master cap_list
              configuration: driver=ahci latency=0
              resources: irq:136 memory:df148000-df149fff memory:df14c000-df14c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:df14b000-df14b7ff
         *-pci:0
              description: PCI bridge
              product: Sunrise Point-H PCI Root Port #17
              vendor: Intel Corporation
              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:122
         *-pci:1
              description: PCI bridge
              product: Sunrise Point-H PCI Express Root Port #1
              vendor: Intel Corporation
              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:123
         *-pci:2
              description: PCI bridge
              product: Sunrise Point-H PCI Express Root Port #3
              vendor: Intel Corporation
              physical id: 1c.2
              bus info: pci@0000:00:1c.2
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:124 memory:df000000-df0fffff
            *-usb
                 description: USB controller
                 product: ASM1142 USB 3.1 Host Controller
                 vendor: ASMedia Technology Inc.
                 physical id: 0
                 bus info: pci@0000:03:00.0
                 version: 00
                 width: 64 bits
                 clock: 33MHz
                 capabilities: msi msix pm pciexpress xhci bus_master cap_list
                 configuration: driver=xhci_hcd latency=0
                 resources: irq:18 memory:df000000-df007fff
               *-usbhost:0
                    product: xHCI Host Controller
                    vendor: Linux 4.8.1-040801-generic xhci-hcd
                    physical id: 0
                    bus info: usb@3
                    logical name: usb3
                    version: 4.08
                    capabilities: usb-2.00
                    configuration: driver=hub slots=2 speed=480Mbit/s
               *-usbhost:1
                    product: xHCI Host Controller
                    vendor: Linux 4.8.1-040801-generic xhci-hcd
                    physical id: 1
                    bus info: usb@4
                    logical name: usb4
                    version: 4.08
                    capabilities: usb-3.00
                    configuration: driver=hub slots=2 speed=5000Mbit/s
         *-pci:3
              description: PCI bridge
              product: Sunrise Point-H PCI Express Root Port #9
              vendor: Intel Corporation
              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:125
         *-pci:4
              description: PCI bridge
              product: Sunrise Point-H PCI Express Root Port #16
              vendor: Intel Corporation
              physical id: 1d.7
              bus info: pci@0000:00:1d.7
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:126
         *-isa
              description: ISA bridge
              product: Sunrise Point-H LPC Controller
              vendor: Intel Corporation
              physical id: 1f
              bus info: pci@0000:00:1f.0
              version: 31
              width: 32 bits
              clock: 33MHz
              capabilities: isa bus_master
              configuration: latency=0
         *-memory UNCLAIMED
              description: Memory controller
              product: Sunrise Point-H PMC
              vendor: Intel Corporation
              physical id: 1f.2
              bus info: pci@0000:00:1f.2
              version: 31
              width: 32 bits
              clock: 33MHz (30.3ns)
              capabilities: bus_master
              configuration: latency=0
              resources: memory:df144000-df147fff
         *-multimedia
              description: Audio device
              product: Sunrise Point-H HD Audio
              vendor: Intel Corporation
              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 31
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi bus_master cap_list
              configuration: driver=snd_hda_intel latency=32
              resources: irq:140 memory:df140000-df143fff memory:df120000-df12ffff
         *-serial UNCLAIMED
              description: SMBus
              product: Sunrise Point-H SMBus
              vendor: Intel Corporation
              physical id: 1f.4
              bus info: pci@0000:00:1f.4
              version: 31
              width: 64 bits
              clock: 33MHz
              configuration: latency=0
              resources: memory:df14a000-df14a0ff ioport:f040(size=32)
         *-network
              description: Ethernet interface
              product: Ethernet Connection (2) I219-V
              vendor: Intel Corporation
              physical id: 1f.6
              bus info: pci@0000:00:1f.6
              logical name: enp0s31f6
              version: 31
              serial: 70:85:c2:0d:78:d2
              capacity: 1Gbit/s
              width: 32 bits
              clock: 33MHz
              capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
              configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
              resources: irq:137 memory:df100000-df11ffff
      *-scsi:0
           physical id: 1
           logical name: scsi0
           capabilities: emulated
         *-disk
              description: ATA Disk
              product: SanDisk SD8SBBU4
              physical id: 0.0.0
              bus info: scsi@0:0.0.0
              logical name: /dev/sda
              version: 6000
              serial: 162873446807
              size: 447GiB (480GB)
              capabilities: partitioned partitioned:dos
              configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=091612ed
            *-volume:0
                 description: Windows FAT volume
                 vendor: mkfs.fat
                 physical id: 1
                 bus info: scsi@0:0.0.0,1
                 logical name: /dev/sda1
                 version: FAT32
                 serial: a493-fb02
                 size: 2047MiB
                 capacity: 2047MiB
                 capabilities: primary bootable fat initialized
                 configuration: FATs=2 filesystem=fat label=BOOT
            *-volume:1
                 description: Windows NTFS volume
                 physical id: 2
                 bus info: scsi@0:0.0.0,2
                 logical name: /dev/sda2
                 version: 3.1
                 serial: 29ac-12e5
                 size: 49GiB
                 capacity: 50GiB
                 capabilities: primary ntfs initialized
                 configuration: clustersize=4096 created=2017-01-18 15:37:02 filesystem=ntfs label=Windows state=clean
            *-volume:2
                 description: EXT4 volume
                 vendor: Linux
                 physical id: 3
                 bus info: scsi@0:0.0.0,3
                 logical name: /dev/sda3
                 logical name: /
                 version: 1.0
                 serial: da422f81-bbd2-4626-92fc-015091aefd3a
                 size: 395GiB
                 capacity: 395GiB
                 capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2017-01-18 16:57:07 filesystem=ext4 lastmountpoint=/ modified=2017-01-20 14:55:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-01-20 14:55:04 state=mounted
      *-scsi:1
           physical id: 2
           logical name: scsi1
           capabilities: emulated
         *-disk
              description: ATA Disk
              product: ST2000DM001-1ER1
              vendor: Seagate
              physical id: 0.0.0
              bus info: scsi@1:0.0.0
              logical name: /dev/sdb
              version: CC26
              serial: W4Z425R6
              size: 1863GiB (2TB)
              capabilities: partitioned partitioned:dos
              configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=45dd4fb4
            *-volume:0
                 description: Linux swap volume
                 physical id: 1
                 bus info: scsi@1:0.0.0,1
                 logical name: /dev/sdb1
                 version: 1
                 serial: ff5bcdb4-e004-491b-844d-17c83bbc1d57
                 size: 64GiB
                 capacity: 64GiB
                 capabilities: primary nofs swap initialized
                 configuration: filesystem=swap pagesize=4096
            *-volume:1
                 description: Windows NTFS volume
                 physical id: 2
                 bus info: scsi@1:0.0.0,2
                 logical name: /dev/sdb2
                 version: 3.1
                 serial: 6d3a-23d2
                 size: 1713GiB
                 capacity: 1799GiB
                 capabilities: primary ntfs initialized
                 configuration: clustersize=4096 created=2017-01-18 15:28:01 filesystem=ntfs label=DataAll modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
      *-scsi:2
           physical id: 3
           logical name: scsi2
           capabilities: emulated
         *-disk
              description: ATA Disk
              product: WDC WD5000AAKS-0
              vendor: Western Digital
              physical id: 0.0.0
              bus info: scsi@2:0.0.0
              logical name: /dev/sdc
              version: 1C02
              serial: WD-WCAS80925828
              size: 465GiB (500GB)
              capabilities: partitioned partitioned:dos
              configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=6ebd6ed2
            *-volume:0
                 description: EXT4 volume
                 vendor: Linux
                 physical id: 1
                 bus info: scsi@2:0.0.0,1
                 logical name: /dev/sdc1
                 version: 1.0
                 serial: 3f8d8efa-83ab-4532-b002-e5c57e3582bd
                 size: 95GiB
                 capacity: 95GiB
                 capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2016-05-15 23:34:49 filesystem=ext4 lastmountpoint=/media/pbarros/3f8d8efa-83ab-4532-b002-e5c57e3582bd modified=2017-01-20 10:55:44 mounted=2017-01-19 14:20:59 state=clean
            *-volume:1
                 description: EXT4 volume
                 vendor: Linux
                 physical id: 2
                 bus info: scsi@2:0.0.0,2
                 logical name: /dev/sdc2
                 version: 1.0
                 serial: ecadfcba-dbf4-4859-8b0e-335a1efb5ba6
                 size: 362GiB
                 capacity: 362GiB
                 capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2016-05-15 23:34:52 filesystem=ext4 lastmountpoint=/media/pbarros/ecadfcba-dbf4-4859-8b0e-335a1efb5ba6 modified=2017-01-20 10:55:44 mounted=2017-01-19 14:21:20 state=clean
            *-volume:2
                 description: Extended partition
                 physical id: 3
                 bus info: scsi@2:0.0.0,3
                 logical name: /dev/sdc3
                 size: 7811MiB
                 capacity: 7811MiB
                 capabilities: primary extended partitioned partitioned:extended
      *-scsi:3
           physical id: 4
           logical name: scsi3
           capabilities: emulated
         *-cdrom
              description: DVD-RAM writer
              product: CDDVDW SH-S203N
              vendor: TSSTcorp
              physical id: 0.0.0
              bus info: scsi@3:0.0.0
              logical name: /dev/cdrom
              logical name: /dev/cdrw
              logical name: /dev/dvd
              logical name: /dev/dvdrw
              logical name: /dev/sr0
              version: SB00
              capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
              configuration: ansiversion=5 status=nodisc
      *-scsi:4
           physical id: 5
           bus info: usb@1:12
           logical name: scsi6
           capabilities: emulated
         *-disk:0
              description: SCSI Disk
              physical id: 0.0.0
              bus info: scsi@6:0.0.0
              logical name: /dev/sdd
              configuration: logicalsectorsize=512 sectorsize=512
         *-disk:1
              description: SCSI Disk
              physical id: 0.0.1
              bus info: scsi@6:0.0.1
              logical name: /dev/sde
              configuration: logicalsectorsize=512 sectorsize=512
         *-disk:2
              description: SCSI Disk
              physical id: 0.0.2
              bus info: scsi@6:0.0.2
              logical name: /dev/sdf
              configuration: logicalsectorsize=512 sectorsize=512
         *-disk:3
              description: SCSI Disk
              physical id: 0.0.3

              bus info: scsi@6:0.0.3
              logical name: /dev/sdg
              configuration: logicalsectorsize=512 sectorsize=512

   *-network
        description: Wireless interface
        physical id: 1
        bus info: usb@1:3

        logical name: wlxa0f3c1238313
        serial: a0:f3:c1:23:83:13
        capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=rt2800usb driverversion=4.8.1-040801-generic firmware=0.29 ip=10.100.20.164 link=yes multicast=yes wireless=IEEE 802.11
```

---

### Post by oldfred on 2017-01-20
Please use code tags on longer text or terminal output.
Easy to add in Forums Advanced Editor and # icon.

Are DIMM exactly same brand/model/speed?
Are you overclocking?
Is power supply large enough?

Try swapping them or just use two not now seen in bank 0 & 2 to see if they work on their own.

You can just print memory.
 sudo lshw | grep -m 1 -A 25 "*-memory" 
sudo lshw -short -C memory

---

### Post by jm33 on 2017-01-20
Thanks a lot!

To your questions:
Are DIMM exactly same brand/model/speed? - YES
Are you overclocking? - NO
Is power supply large enough? MAYBE NOT. Will try to get a more powerful one

I have swapped the DIIMs, but result is exactly the same....

I thought you would like to see all the output of lshw...
Sorry for the code tags, will do it better next time.

---

### Post by jm33 on 2017-01-22
OK, now I got a more powerful power supply, and still nothing....
Any other suggestions?
Thank you for your time

---

### Post by oldfred on 2017-01-22
Are there any special rules on how you populate the banks?
If UEFI/BIOS sees them, it should be ok.

Did you try with each bank alone, then in combination?

Not sure what else to suggest.

---

### Post by The Cog on 2017-01-22
It might be interesting to swap the first pair with the second pair. If the memory that Linux sees moves then there is something different about the RAM sticks. If the memory appears to stay in the same place (so that the sticks that you could see are no longer detected) then there is something up with the motherboard. If it's something to do with the motherboard then I don't know what to suggest, but it may at least help to know.

---

### Post by Yellow Pasque on 2017-01-22
> CMK16GX4M2A2400C14
Asrock lists the modules as only testing successfully with 2 sticks. [http://asrock.com/mb/Intel/Z170%20Extreme4/?cat=Memory](http://asrock.com/mb/Intel/Z170%20Extreme4/?cat=Memory)
Which leads me to believe that either they didn't try 4 sticks or had issues when using 4 sticks.

---

### Post by jm33 on 2017-01-29
OK, I tested a new Processor in the same mobo and it saw all my 32 GB Ram. It is clearly a problem with the BIOS that does not yet work properly with the Kaby Lake processors.
Got a new mobo (ASUS Z270-A) and it works perfectly.
Thanks a lot for all the help.

---

