---
title: "slow to no boot"
date: 2022-05-11
forum: General Help
---

### Post by chris-verdon on 2022-05-11
I'm helping a friend with their system and the problem is lately when it powers up it hangs on the motherboard splash screen. Sometimes we can get it to grub and then to recovery mode. We've tried using systemd-analze to see where it's getting hung up and we got the "bootup is not yet finished" error. Checked systemctl to see if there's anything stuck and it says dev-fuse.device is "loading activating tentative" so I think that's why we can't do the analysis. It's running 18.04 lts on an Intel 1tb nvme ssd. We both would appreciate all the help we can get on this.

edit: more info
```
computer                    
    description: Desktop Computer
    product: B450M DS3H (Default string)
    vendor: Gigabyte Technology Co., Ltd.
    version: Default string
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: boot=normal chassis=desktop family=Default string sku=Default string uuid=[REMOVED]
  *-core
       description: Motherboard
       product: B450M DS3H-CF
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: [REMOVED]
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F2
          date: 08/08/2018
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             product: Unknown
             vendor: Unknown
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 0
        *-bank:1
             description: [empty]
             product: Unknown
             vendor: Unknown
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 1
        *-bank:2
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: F4-2133C15-4GNT
             vendor: Unknown
             physical id: 2
             serial: [REMOVED]
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:3
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: F4-2133C15-4GNT
             vendor: Unknown
             physical id: 3
             serial: [REMOVED]
             slot: DIMM 1
             size: 4GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-cache:0
          description: L1 cache
          physical id: 28
          slot: L1 - Cache
          size: 384KiB
          capacity: 384KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 29
          slot: L2 - Cache
          size: 2MiB
          capacity: 2MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 2a
          slot: L3 - Cache
          size: 4MiB
          capacity: 4MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: AMD Ryzen 3 2200G with Radeon Vega Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 2b
          bus info: cpu@0
          version: AMD Ryzen 3 2200G with Radeon Vega Graphics
          serial: [REMOVED]
          slot: AM4
          size: 1482MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate sme ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:f000(size=4096) memory:fe600000-fe7fffff ioport:f0300000(size=1048576)
           *-usb
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: msi pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:37 memory:fe7a0000-fe7a7fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-154-generic xhci-hcd
                   physical id: 0
                   bus info: usb@1
                   logical name: usb1
                   version: 4.15
                   capabilities: usb-2.00
                   configuration: driver=hub slots=10 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      vendor: Holtek Semiconductor, Inc.
                      physical id: 1
                      bus info: usb@1:1
                      version: 1.15
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
                 *-usb:1
                      description: Mouse
                      product: ELECOM Relacon
                      vendor: ELECOM
                      physical id: 2
                      bus info: usb@1:2
                      version: 10.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:2
                      description: Mouse
                      product: TWA60
                      vendor: UC-LOGIC
                      physical id: 4
                      bus info: usb@1:4
                      version: 0.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:3
                      description: Mass storage device
                      product: Ext HDD 1021
                      vendor: Western Digital
                      physical id: 5
                      bus info: usb@1:5
                      logical name: scsi11
                      version: 20.02
                      serial: [REMOVED]
                      capabilities: usb-2.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=2mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: Ext HDD 1021
                         vendor: WD
                         physical id: 0.0.0
                         bus info: scsi@11:0.0.0
                         logical name: /dev/sdc
                         version: 2002
                         serial: [REMOVED]
                         configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-154-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 4.15
                   capabilities: usb-3.10
                   configuration: driver=hub slots=4 speed=10000Mbit/s
           *-storage
                description: SATA controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:50 memory:fe780000-fe79ffff memory:fe700000-fe77ffff
           *-pci
                description: PCI bridge
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:31 ioport:f000(size=4096) memory:fe600000-fe6fffff ioport:f0300000(size=1048576)
              *-pci:0
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 0
                   bus info: pci@0000:02:00.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:33
              *-pci:1
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 1
                   bus info: pci@0000:02:01.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:35 ioport:f000(size=4096) memory:fe600000-fe6fffff ioport:f0300000(size=1048576)
                 *-network
                      description: Ethernet interface
                      product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                      vendor: Realtek Semiconductor Co., Ltd.
                      physical id: 0
                      bus info: pci@0000:04:00.0
                      logical name: enp4s0
                      version: 0c
                      serial: [REMOVED]
                      size: 100Mbit/s
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                      resources: irq:34 ioport:f000(size=256) memory:fe600000-fe600fff memory:f0300000-f0303fff
              *-pci:2
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 4
                   bus info: pci@0000:02:04.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:36
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:fe900000-fe9fffff
           *-storage
                description: Non-Volatile memory controller
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:51 memory:fe900000-fe903fff
              *-nvme0
                   description: NVMe device
                   product: INTEL SSDPEKNW010T9
                   physical id: 0
                   logical name: /dev/nvme0
                   version: 001C
                   serial: [REMOVED]
                   configuration: nqn=nqn.2010-36.com.intel:nvm-subsystem-sn-btnr0364104f1p0b state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
                      size: 953GiB (1024GB)
                      capabilities: gpt-1.00 partitioned partitioned:gpt
                      configuration: guid=1f01fe97-b214-4c23-a00f-87fc0c7a47ad logicalsectorsize=512 sectorsize=512
                    *-volume:0
                         description: Windows FAT volume
                         vendor: mkfs.fat
                         physical id: 1
                         logical name: /dev/nvme0n1p1
                         version: FAT32
                         serial: [REMOVED]
                         size: 510MiB
                         capacity: 511MiB
                         capabilities: boot fat initialized
                         configuration: FATs=2 filesystem=fat name=EFI System Partition
                    *-volume:1
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 2
                         logical name: /dev/nvme0n1p2
                         version: 1.0
                         serial: [REMOVED]
                         size: 953GiB
                         capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                         configuration: created=2021-09-01 11:20:49 filesystem=ext4 lastmountpoint=/media/redacted/7e4c96ac-e3b9-4247-baf6-e390e6f175a7 modified=2022-05-11 12:41:50 mounted=2022-05-11 12:41:50 state=clean
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) memory:fe200000-fe5fffff ioport:e0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:07:00.0
                version: c8
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list rom
                configuration: driver=amdgpu latency=0
                resources: irq:67 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe500000-fe57ffff memory:c0000-dffff
           *-multimedia:0
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD/ATI]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:07:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:66 memory:fe588000-fe58bfff
           *-generic UNCLAIMED
                description: Encryption controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:07:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: latency=0
                resources: memory:fe400000-fe4fffff memory:fe58c000-fe58dfff
           *-usb:0
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:07:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:38 memory:fe300000-fe3fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-154-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 4.15
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-154-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 4.15
                   capabilities: usb-3.10
                   configuration: driver=hub slots=4 speed=10000Mbit/s
                 *-usb
                      description: Mass storage device
                      product: Game Drive
                      vendor: Western Digital
                      physical id: 3
                      bus info: usb@4:3
                      logical name: scsi1
                      version: 50.02
                      serial: [REMOVED]
                      capabilities: usb-3.10 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=896mA speed=5000Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: Game Drive
                         vendor: WD
                         physical id: 0.0.0
                         bus info: scsi@1:0.0.0
                         logical name: /dev/sdb
                         version: 5002
                         serial: [REMOVED]
                         size: 3725GiB (4TB)
                         capabilities: gpt-1.00 partitioned partitioned:gpt
                         configuration: ansiversion=6 guid=960b3cc7-a178-44ca-8402-5b94382abf01 logicalsectorsize=512 sectorsize=4096
                       *-volume
                            description: data partition
                            vendor: Windows
                            physical id: 1
                            bus info: scsi@1:0.0.0,1
                            logical name: /dev/sdb1
                            logical name: /media/redacted/WD_BLACK
                            serial: [REMOVED]
                            capacity: 3725GiB
                            configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 name=WD_BLACK state=mounted
           *-usb:1
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.4
                bus info: pci@0000:07:00.4
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:44 memory:fe200000-fe2fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-154-generic xhci-hcd
                   physical id: 0
                   bus info: usb@5
                   logical name: usb5
                   version: 4.15
                   capabilities: usb-2.00
                   configuration: driver=hub slots=1 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-154-generic xhci-hcd
                   physical id: 1
                   bus info: usb@6
                   logical name: usb6
                   version: 4.15
                   capabilities: usb-3.10
                   configuration: driver=hub slots=1 speed=10000Mbit/s
           *-multimedia:1
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.6
                bus info: pci@0000:07:00.6
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:52 memory:fe580000-fe587fff
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 memory:fe800000-fe8fffff
           *-storage
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress msi ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:55 memory:fe800000-fe8007ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 61
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500312CS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SC13
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=d305502f-02d5-4920-9081-116f5c41f7de logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 465GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-01-21 00:47:03 filesystem=ext4 lastmountpoint=/ modified=2022-05-11 12:30:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2022-05-11 12:30:32 state=mounted
```

---

### Post by laurel798 on 2022-05-11
Gonna keep an eye on your post to see if anyone has any thoughts- sorry I'm of no help myself. Having similar issues on a Ryzen 7 5000 Series, AMD graphics, Asus Vivobook 15, no matter what distro or kernel I try.

---

### Post by chris-verdon on 2022-05-12
we're still working on this. It's worth noting when we ran list hardware  we were running an older version from a backup drive so while it says  it's running 18.04, what we're actually trying to fix is a 22.04 install

---

### Post by oldfred on 2022-05-12
Converted quote to code tags.
Easy to add code tags with Forum's Go Advanced and # icon.

Many have required UEFI firmware updates.
And if SSD, SSD firmware updates.

Many AMD systems need IOMMU settings.

While different brands, some issues are common to chip set.
If 22.04, this should not be an issue.
Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247) & 
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)

 MSI B450M Pro-Vdh Max Unable to install Ubuntu (Black Screen)  UEFI update required
[https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556](https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556)
Asus B450 ROG STRIX B450-F 
[https://ubuntuforums.org/showthread.php?t=2460822](https://ubuntuforums.org/showthread.php?t=2460822)
Asus B450-F Clock speeds
[https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363](https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363)
Asus ROG strix b450-F
[https://askubuntu.com/questions/1267714/error-while-trying-to-install-any-linux-version-ubuntu-ubuntu-budgie-solus-gn?noredirect=1#comment2146118_1267714](https://askubuntu.com/questions/1267714/error-while-trying-to-install-any-linux-version-ubuntu-ubuntu-budgie-solus-gn?noredirect=1#comment2146118_1267714)
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

---

### Post by chris-verdon on 2022-05-12
ok, we'll try and work through these and see where it takes us. Meanwhile we finally got systemd-analyze to run. Output doesn't looks like it reveals much
```
'Startup finished in 6min 11.224s (firmware) + 33min 41.947s (loader) +  6.902s (kernel) + 1h 31min 8.438s (userspace) = 2h 11min 8.512s graphical.target reached after 1min 19.127s in userspace'
```

---

### Post by #&amp;thj^% on 2022-05-12
> **oldfred said:**
> 

Many AMD systems need IOMMU settings.


+1
one worth a mention would be <amd_iommu_intr= legacy >
legacy     - Use legacy interrupt remapping mode.
Just a stab is all.

---

### Post by oldfred on 2022-05-12
Most of this is the same settings, but that may show what works.

Some more things to work thru.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by chris-verdon on 2022-05-12
Thanks for the help so far. We're already getting some results. I'll make sure to acknowledge the thread as solved once we're sure.

---

