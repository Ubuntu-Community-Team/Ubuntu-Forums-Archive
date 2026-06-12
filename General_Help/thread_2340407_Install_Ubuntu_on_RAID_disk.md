---
title: "Install Ubuntu on RAID disk"
date: 2016-10-18
forum: General Help
---

### Post by matiazz on 2016-10-18
Hi there, i'm trying to install ubuntu on a raid disk(i have windows 8, i prefer only ubuntu, if not dual). I alredy post here ([https://ubuntuforums.org/showthread.php?t=2339885&p=13556370#post13556370](https://ubuntuforums.org/showthread.php?t=2339885&p=13556370#post13556370)) and they recomend me doing one here.

The problem is that in the screen that i can make the partition and choose in which hard drive or ssd i want to install(i don't know if i have one of each or a hybrid), there is nothing, like if i havent any disk. 
Like you can see here:
[[IMG]https://s18.postimg.org/y28lopx45/IMG_1925.jpg[/IMG]]("https://postimg.org/image/y28lopx45/")

Here is the  [COLOR=#000000] lshw.txt [/COLOR]that they make me do in a live boot of ubuntu:[COLOR=#000000]
[/COLOR]
```
computer
    description: Computer
    width: 64 bits
    capabilities: smbios-2.7 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3833MiB
     *-cpu
          product: Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 863MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts cpufreq
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:c4000000-c43fffff memory:b0000000-bfffffff ioport:5000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:24 memory:c4500000-c450ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 0
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:29 memory:c4514000-c451400f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:c4519000-c45193ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-21-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb:0
                      description: Human interface device
                      product: Touchscreen
                      vendor: ELAN
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 80.15
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      product: Bluetooth USB Host Controller
                      vendor: Atheros Communications
                      physical id: 2
                      bus info: usb@1:1.2
                      version: 0.02
                      serial: [REMOVED]
                      capabilities: bluetooth usb-1.10
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
                 *-usb:2
                      description: Video
                      product: USB2.0 Camera
                      vendor: 56180066012ABAST
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 0.13
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=200mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:30 memory:c4510000-c4513fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:c3000000-c3ffffff ioport:c0000000(size=16777216)
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.4.0-21-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:c3000000-c307ffff memory:c3080000-c308ffff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:c2000000-c2ffffff ioport:c1000000(size=16777216)
           *-generic
                description: Unassigned class
                product: RTS5209 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:25 memory:c2000000-c2000fff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) ioport:c4400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: enp14s0
                version: 07
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:26 ioport:2000(size=256) memory:c4404000-c4404fff memory:c4400000-c4403fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:c4518000-c45183ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-21-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb
                      description: Mass storage device
                      product: Mass Storage
                      vendor: Generic
                      physical id: 2
                      bus info: usb@2:1.2
                      logical name: scsi6
                      version: 1.09
                      serial: [REMOVED]
                      capabilities: usb-2.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         physical id: 0.0.0
                         bus info: scsi@6:0.0.0
                         logical name: /dev/sdc
                         size: 3900MiB (4089MB)
                         capabilities: partitioned partitioned:dos
                         configuration: logicalsectorsize=512 sectorsize=512 signature=01e2fba6
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            bus info: scsi@6:0.0.0,1
                            logical name: /dev/sdc1
                            logical name: /cdrom
                            version: FAT32
                            serial: [REMOVED]
                            size: 3897MiB
                            capacity: 3899MiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=UBUNTU 16_0 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
        *-isa
             description: ISA bridge
             product: HM77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:5088(size=8) ioport:5094(size=4) ioport:5080(size=8) ioport:5090(size=4) ioport:5060(size=32) memory:c4517000-c45177ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c4515000-c45150ff ioport:5040(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54323
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A90C
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=8e4eb3a3-e936-4683-8d22-ca8106f89358 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT32
                serial: [REMOVED]
                size: 255MiB
                capacity: 259MiB
                capabilities: precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat label=SONYSYS name=EFI system partition
           *-volume:1
                description: Windows NTFS volume
                vendor: Windows
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 1468MiB
                capacity: 1473MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2012-12-05 20:06:22 filesystem=ntfs label=Windows RE tools name=Basic data partition state=clean
           *-volume:2
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: FAT32
                serial: [REMOVED]
                size: 248MiB
                capacity: 259MiB
                capabilities: boot precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat name=EFI system partition
           *-volume:3
                description: reserved partition
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                serial: [REMOVED]
                capacity: 127MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: [REMOVED]
                size: 272GiB
                capacity: 272GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2016-10-12 18:25:18 filesystem=ntfs name=Basic data partition state=clean
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: [REMOVED]
                size: 23GiB
                capacity: 23GiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2012-12-05 20:06:46 filesystem=ntfs label=Recovery modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG MZMPC032
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 201Q
             serial: [REMOVED]
             size: 29GiB (32GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=60c81f15-0f4f-449a-8e4f-2d5a0bf5b6d8 logicalsectorsize=512 sectorsize=512
           *-volume
                description: EFI partition
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                serial: [REMOVED]
                capacity: 11GiB
                capabilities: precious readonly hidden nomount
                configuration: name=Basic data partition
```
I try also with debian and windows 7 only to make me sure that is a problem of my pc and not of ubuntu. With this i have the same result like before.

Any ideas?

thx

---

