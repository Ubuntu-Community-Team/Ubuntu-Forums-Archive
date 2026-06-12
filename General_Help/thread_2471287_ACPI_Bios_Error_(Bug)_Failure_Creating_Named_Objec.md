---
title: "ACPI Bios Error (Bug) Failure Creating Named Object"
date: 2022-01-25
forum: General Help
---

### Post by webmanoffesto on 2022-01-25
Can I repair this install of Lubuntu? What do you recommend I do?

Error: ACPI Bios Error (Bug) Failure Creating Named Object

ScreenCap here [https://ibb.co/zsrWqbX](https://ibb.co/zsrWqbX)

lshw
```

sudo lshw
lubuntu                     
    description: Notebook
    product: HP Laptop 17-cn0xxx (316H8UA#ABA)
    vendor: HP
    version: Chassis Version
    serial: 5CG1182M5K
    width: 64 bits
    capabilities: smbios-3.3.0 dmi-3.3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV HP Notebook sku=316H8UA#ABA uuid=BA81200F-18D2-4CEC-958C-C302B29F3CAA
  *-core
       description: Motherboard
       product: 883C
       vendor: HP
       physical id: 0
       version: 69.16
       serial: PLKTR00WBF53NK
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: AMI
          physical id: 0
          version: F.04
          date: 04/01/2021
          size: 64KiB
          capacity: 8MiB
          capabilities: pci upgrade shadowing cdboot bootselect edd smartbattery biosbootspecification netboot uefi
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 3200 MHz (0.3 ns)
             product: HMA851S6DJR6N-XN
             vendor: SK Hynix
             physical id: 0
             serial: 23A0F665
             slot: Bottom - Slot 1 (left)
             size: 4GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous 3200 MHz (0.3 ns)
             product: HMA81GS6CJR8N-XN
             vendor: SK Hynix
             physical id: 1
             serial: 239689BB
             slot: Bottom - Slot 2 (right)
             size: 8GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
     *-cache:0
          description: L1 cache
          physical id: 2a
          slot: L1 Cache
          size: 192KiB
          capacity: 192KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 2b
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 2c
          slot: L2 Cache
          size: 5MiB
          capacity: 5MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 2d
          slot: L3 Cache
          size: 8MiB
          capacity: 8MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: 11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz
          vendor: Intel Corp.
          physical id: 2e
          bus info: cpu@0
          version: 11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1244MHz
          capacity: 4200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb cat_l2 invpcid_single cdp_l2 ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdt_a avx512f avx512dq rdseed adx smap avx512ifma clflushopt clwb intel_pt avx512cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves split_lock_detect dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp hwp_pkg_req avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg avx512_vpopcntdq rdpid movdiri movdir64b fsrm avx512_vp2intersect md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             logical name: /dev/fb0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
             configuration: depth=32 driver=i915 latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
             resources: iomemory:600-5ff iomemory:400-3ff irq:145 memory:6002000000-6002ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: iomemory:600-5ff irq:16 memory:6003200000-600321ffff
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: latency=0
             resources: iomemory:600-5ff memory:6003245000-6003245fff
        *-generic:2
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress pm cap_list
             configuration: driver=intel-pmt latency=0
             resources: iomemory:600-5ff irq:0 memory:6003230000-6003237fff
        *-raid
             description: RAID bus controller
             product: Volume Management Device NVMe RAID Controller
             vendor: Intel Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: raid msix pciexpress pm bus_master cap_list
             configuration: driver=vmd latency=0
             resources: iomemory:600-5ff iomemory:600-5ff irq:0 memory:6000000000-6001ffffff memory:52000000-53ffffff memory:6003100000-60031fffff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: iomemory:600-5ff irq:142 memory:6003220000-600322ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.11.0-27-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.11
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Cruzer
                   vendor: SanDisk
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.02
                   serial: 200607752113C0F0A48B
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
              *-usb:1
                   description: Video
                   product: HP TrueVision HD Camera
                   physical id: 5
                   bus info: usb@1:5
                   version: 27.47
                   serial: 0001
                   capabilities: usb-2.01
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   product: Bluetooth Radio
                   vendor: Realtek
                   physical id: a
                   bus info: usb@1:a
                   version: 1.10
                   serial: 00e04c000001
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=500mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.11.0-27-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.11
                capabilities: usb-3.10
                configuration: driver=hub slots=4 speed=10000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 20
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: iomemory:600-5ff iomemory:600-5ff memory:600323c000-600323ffff memory:6003244000-6003244fff
        *-serial:0
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:27 memory:4017000000-4017000fff
        *-serial:1
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:40 memory:4017001000-4017001fff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: iomemory:600-5ff irq:146 memory:6003241000-6003241fff
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-pci
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:3000(size=4096) memory:54000000-540fffff
           *-network
                description: Wireless interface
                product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 00
                serial: 80:d2:1d:f3:d3:43
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtw_8821ce driverversion=5.11.0-27-generic firmware=N/A ip=192.168.1.198 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:148 ioport:3000(size=256) memory:54000000-5400ffff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=sof-audio-pci latency=32
             resources: iomemory:600-5ff iomemory:600-5ff irq:147 memory:6003238000-600323bfff memory:6003000000-60030fffff
        *-serial:2
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 20
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:600-5ff irq:16 memory:6003240000-60032400ff ioport:efa0(size=32)
        *-serial:3 UNCLAIMED
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 20
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:50400000-50400fff
     *-sata
          description: SATA controller
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 17
          version: 20
          width: 32 bits
          clock: 66MHz
          capabilities: sata msi pm ahci_1.0 bus_master cap_list
          configuration: driver=ahci latency=0
          resources: irq:144 memory:52000000-52001fff memory:52002800-520028ff memory:52002000-520027ff
     *-pnp00:00
          product: PnP device HPQ8001
          physical id: 1
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0b00
          physical id: 3
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:03
          product: PnP device INT3f0d
          physical id: 4
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device PNP0c02
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0c02
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-pnp00:07
          product: PnP device PNP0c02
          physical id: 8
          capabilities: pnp
          configuration: driver=system
     *-scsi:0
          physical id: 9
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ04ABF1
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 7C
             serial: 31J6P7X2T
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=b2c53b6c-481c-44b8-b279-c89c3fa17cdf logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: FAT32
                serial: 6c1e-1800
                size: 255MiB
                capacity: 259MiB
                capabilities: boot nomount fat initialized
                configuration: FATs=2 filesystem=fat label=SYSTEM name=EFI system partition
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: 0046e394-f790-4500-84b8-005196c74c35
                size: 24GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2021-10-17 15:07:05 filesystem=ext4 label=Root lastmountpoint=/ modified=2022-01-21 17:22:59 mounted=2022-01-21 17:23:03 state=clean
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: bcf58f61-2ad3-4c96-8621-dd2f220bc709
                size: 906GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2021-10-17 15:07:11 filesystem=ext4 label=Home lastmountpoint=/media/lubuntu/Home modified=2022-01-21 17:23:13 mounted=2022-01-14 14:23:40 state=unknown
     *-scsi:1
          physical id: a
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Cruzer
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.10
             size: 29GiB (32GB)
             capabilities: removable
             configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 29GiB (32GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=665ef902
              *-volume:0
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 2
                   logical name: /dev/sdb2
                   version: FAT12
                   serial: 54c5-9c6c
                   size: 15EiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   logical name: /dev/sdb3
                   logical name: /var/log
                   logical name: /var/crash
                   version: 1.0
                   serial: 8b02ff77-dbab-401b-8c31-51667d9ce2be
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2021-10-12 00:42:29 filesystem=ext4 label=writable lastmountpoint=/root/var/crash modified=2022-01-25 16:55:32 mount.fstype=ext4 mount.options=rw,relatime mounted=2022-01-25 16:55:32 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: HW03041X
       vendor: 313-1D-33-A
       physical id: 1
       version: 02/22/2021
       serial: 03732 02/22/2021
       slot: Primary
       capacity: 41050mWh
       configuration: voltage=11.3V


```


lscpi
```

 lspci
0000:00:00.0 Host bridge: Intel Corporation Device 9a14 (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation Device 9a49 (rev 01)
0000:00:04.0 Signal processing controller: Intel Corporation Device 9a03 (rev 01)
0000:00:08.0 System peripheral: Intel Corporation Device 9a11 (rev 01)
0000:00:0a.0 Signal processing controller: Intel Corporation Device 9a0d (rev 01)
0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller
0000:00:14.0 USB controller: Intel Corporation Device a0ed (rev 20)
0000:00:14.2 RAM memory: Intel Corporation Device a0ef (rev 20)
0000:00:15.0 Serial bus controller [0c80]: Intel Corporation Device a0e8 (rev 20)
0000:00:15.1 Serial bus controller [0c80]: Intel Corporation Device a0e9 (rev 20)
0000:00:16.0 Communication controller: Intel Corporation Device a0e0 (rev 20)
0000:00:17.0 System peripheral: Intel Corporation Device 09ab
0000:00:1d.0 PCI bridge: Intel Corporation Device a0b0 (rev 20)
0000:00:1f.0 ISA bridge: Intel Corporation Device a082 (rev 20)
0000:00:1f.3 Multimedia audio controller: Intel Corporation Device a0c8 (rev 20)
0000:00:1f.4 SMBus: Intel Corporation Device a0a3 (rev 20)
0000:00:1f.5 Serial bus controller [0c80]: Intel Corporation Device a0a4 (rev 20)
0000:01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter
10000:e0:17.0 SATA controller: Intel Corporation Device a0d3 (rev 20)


```

---

