---
title: "Boot Logo, Splash Screen Issue"
date: 2017-03-04
forum: General Help
---

### Post by natesnape on 2017-03-04
Hello guys I'm having a bit of dilemma with my Boot logo and/or Splash Screen, when I was using the Open source Nvidia driver the boot logo and/or splash screen is the same size as the resolution of my PC 1440x900, however when I installed the Nvidia Proprietary driver, they changed to something like 640x480, Is there a way to change the size without going back to the open sourced drivers?

---

### Post by mörgæs on 2017-03-04
Which Nvidia? Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by efflandt on 2017-03-04
The Ubuntu logo with dots under it at various times sometimes displays with a generic font instead of the Ubuntu font when using nvidia drivers. But you have given not clue what your graphics card is or which nvidia driver package you are using.

Also is your display digitally connected with DVI or HDMI (which should be able to automatically determine resolution) or VGA (which cannot being analog)? Is your desktop the proper resolution for login and after that?

---

### Post by natesnape on 2017-03-04
```

computer    description: Desktop Computer
    product: P4M900T-M2 (To Be Filled By O.E.M.)
    vendor: ECS
    version: 2.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: P4M900T-M2
       vendor: ECS
       physical id: 0
       version: 2.0
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014
          date: 08/18/2008
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
          serial: [REMOVED]
          slot: CPU 1
          size: 1203MHz
          capacity: 2003MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf eagerfpu pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 2GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f0000000-f7ffffff
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode cap_list
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:fd000000-feafffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF108 [GeForce GT 630]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:26 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:ec00(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GF108 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:27 memory:feafc000-feafffff
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:cbf00000-cc0fffff ioport:cc100000(size=2097152)
        *-ide:0
             description: IDE interface
             product: VT8237/8251 Serial ATA Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=64
             resources: irq:21 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) ioport:d000(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-usb:0
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:20 ioport:c480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-39-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:22 ioport:c800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-39-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:c880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-39-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:23 ioport:cc00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-39-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:21 memory:fcfffc00-fcfffcff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-39-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: StoreJet Transcend
                   vendor: StoreJet Transcend
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi4
                   version: 80.00
                   serial: [REMOVED]
                   capabilities: usb-2.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Transcend
                      vendor: StoreJet
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdd
                      version: 0
                      serial: [REMOVED]
                      size: 931GiB (1TB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=002f3d1e
                    *-volume
                         description: Windows NTFS volume
                         physical id: 1
                         bus info: scsi@4:0.0.0,1
                         logical name: /dev/sdd1
                         logical name: /media/natesnape/Lone
                         version: 3.1
                         serial: [REMOVED]
                         size: 931GiB
                         capacity: 931GiB
                         capabilities: primary bootable ntfs initialized
                         configuration: clustersize=4096 created=2013-08-26 04:58:25 filesystem=ntfs label=Lone modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
              *-usb:1
                   description: Mass storage device
                   product: BUP Slim SL
                   vendor: Seagate
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi5
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.10 scsi
                   configuration: driver=uas maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: BUP Slim SL
                      vendor: Seagate
                      physical id: 0.0.0
                      bus info: scsi@5:0.0.0
                      logical name: /dev/sdc
                      version: 0302
                      serial: [REMOVED]
                      size: 1863GiB (2TB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=4096 signature=1bb4def4
                    *-volume
                         description: Windows NTFS volume
                         physical id: 1
                         bus info: scsi@5:0.0.0,1
                         logical name: /dev/sdc1
                         logical name: /media/natesnape/Wanderer
                         version: 3.1
                         serial: [REMOVED]
                         size: 1863GiB
                         capacity: 1863GiB
                         capabilities: primary bootable ntfs initialized
                         configuration: clustersize=4096 created=2015-02-12 20:10:44 filesystem=ntfs label=Wanderer mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-usb:2
                   description: Mass storage device
                   product: Elements 1023
                   vendor: Western Digital
                   physical id: 3
                   bus info: usb@1:3
                   logical name: scsi6
                   version: 20.05
                   serial: [REMOVED]
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Elements 1023
                      vendor: WD
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sde
                      version: 2005
                      serial: [REMOVED]
                      size: 465GiB (500GB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512 signature=00029aa0
                    *-volume
                         description: Windows NTFS volume
                         physical id: 1
                         bus info: scsi@6:0.0.0,1
                         logical name: /dev/sde1
                         logical name: /media/natesnape/Courier
                         version: 3.1
                         serial: [REMOVED]
                         size: 465GiB
                         capacity: 465GiB
                         capabilities: primary ntfs initialized
                         configuration: clustersize=4096 created=2010-03-22 10:40:48 filesystem=ntfs label=Courier mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102/VT6103 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: enp0s18
             version: 7c
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:c000(size=256) memory:fcfff800-fcfff8ff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8237/8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=128
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT8237A/VT8251 HDA Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=snd_hda_intel latency=0
          resources: irq:17 memory:febfc000-febfffff
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160815AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: B
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0f000eff
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 149GiB
                capacity: 149GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-05-28 09:07:01 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160215AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: A
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=bab9bab9
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                version: 1.0
                serial: [REMOVED]
                size: 88GiB
                capacity: 149GiB
                capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2017-03-03 10:48:27 filesystem=ext4 modified=2017-03-03 10:48:28 state=clean
              *-logicalvolume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 5
                   logical name: /dev/sdb5
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 145GiB
                   capacity: 145GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                   configuration: created=2017-02-27 11:57:54 filesystem=ext4 lastmountpoint=/ modified=2017-03-05 07:40:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-03-04 14:20:29 state=mounted
              *-logicalvolume:1
                   description: Linux swap volume
                   physical id: 6
                   logical name: /dev/sdb6
                   version: 1
                   serial: [REMOVED]
                   size: 3260MiB
                   capacity: 3260MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096



```

Like this? I have the Nvidia 367.57

---

### Post by natesnape on 2017-03-04
> **efflandt said:**
> The Ubuntu logo with dots under it at various times sometimes displays with a generic font instead of the Ubuntu font when using nvidia drivers. But you have given not clue what your graphics card is or which nvidia driver package you are using.

Also is your display digitally connected with DVI or HDMI (which should be able to automatically determine resolution) or VGA (which cannot being analog)? Is your desktop the proper resolution for login and after that? 
I have a GT 630 connected Via VGA, and after the boot screen my monitor will have the default 1400x900 resolution.

---

