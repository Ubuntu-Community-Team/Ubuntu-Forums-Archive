---
title: "New install: Mouse action fails and computer hangs"
date: 2021-05-28
forum: General Help
---

### Post by makem2 on 2021-05-28
Today installed xubuntu as a dual boot with windows 10. For most of the time setting xubuntu up everything went well, no problems.

Then a problem with mouse selections not working started and it was impossible to select anything. The only escape was a hard shut down. This has occurred several times between which everything appears normal and no errors seen.

The mouse is a G903 and has been performing without fault on a laptop. I am using the mouse dongle from the laptop.

I need to determine if this is a software problem. The machine was built to spec by pcsystems.

At the moment the xubuntu install has only progressed as far as installing a browser and email program. All drivers are default.

Crash log:

```

makem@makem-pc:~$ ls -la /var/crash
total 460
drwxrwsrwt  2 root     whoopsie   4096 May 29 00:43 .
drwxr-xr-x 14 root     root       4096 Feb  9 19:08 ..
-rw-r-----  1 makem    whoopsie  85142 May 28 23:00 _usr_bin_blueman-tray.1000.crash
-rw-rw-r--  1 makem    whoopsie      0 May 28 23:00 _usr_bin_blueman-tray.1000.upload
-rw-------  1 whoopsie whoopsie     37 May 28 23:00 _usr_bin_blueman-tray.1000.uploaded
-rw-r-----  1 root     whoopsie 368837 May 29 00:43 _usr_lib_xorg_Xorg.0.crash
makem@makem-pc:~$

```

System Info:

```

makem@makem-pc:~$ uname -v
#60~20.04.1-Ubuntu SMP Thu May 6 09:52:46 UTC 2021
makem@makem-pc:~$ sudo lshw
[sudo] password for makem: 
makem-pc                    
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: ASUS
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-3.3.0 dmi-3.3.0 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=CAE6F543-0F1A-DD86-960E-F02F74DBDEF1
  *-core
       description: Motherboard
       product: TUF GAMING Z590-PLUS WIFI
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: 210281430900687
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0811
          date: 04/06/2021
          size: 64KiB
          capacity: 24MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer int10video usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 47
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5) [empty]
             physical id: 0
             slot: Controller0-ChannelA-DIMM0
        *-bank:1
             description: DIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: CM4X8GD3200C16K4
             vendor: Corsair
             physical id: 1
             serial: 00000000
             slot: Controller0-ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:2
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5) [empty]
             physical id: 2
             slot: Controller0-ChannelB-DIMM0
        *-bank:3
             description: DIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: CM4X8GD3200C16K4
             vendor: Corsair
             physical id: 3
             serial: 00000000
             slot: Controller0-ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-cache:0
          description: L1 cache
          physical id: 58
          slot: L1 Cache
          size: 384KiB
          capacity: 384KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 59
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 5a
          slot: L2 Cache
          size: 4MiB
          capacity: 4MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 5b
          slot: L3 Cache
          size: 16MiB
          capacity: 16MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: 11th Gen Intel(R) Core(TM) i7-11700K @ 3.60GHz
          vendor: Intel Corp.
          physical id: 5c
          bus info: cpu@0
          version: 11th Gen Intel(R) Core(TM) i7-11700K @ 3.60GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1200
          size: 4076MHz
          capacity: 4900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx avx512f avx512dq rdseed adx smap avx512ifma clflushopt intel_pt avx512cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp hwp_pkg_req avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg avx512_vpopcntdq rdpid fsrm md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=8 enabledcores=8 threads=16
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: iomemory:600-5ff iomemory:400-3ff memory:6000000000-6000ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: iomemory:600-5ff irq:127 memory:6001100000-600110ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.8.0-53-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.08
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: CORSAIR K63 Wireless USB Receiver
                   vendor: CORSAIR
                   physical id: 4
                   bus info: usb@1:4
                   version: 3.13
                   serial: 13009017AF2520C75A368313F5001BC5
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 6
                   bus info: usb@1:6
                   version: 60.60
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
              *-usb:2
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 7
                   bus info: usb@1:7
                   version: 39.06
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:3
                   description: Audio device
                   product: SteelSeries Arctis 1 Wireless
                   vendor: SteelSeries
                   physical id: 8
                   bus info: usb@1:8
                   version: 1.05
                   capabilities: usb-1.10 audio-control
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:4
                   description: Human interface device
                   product: AURA LED Controller
                   vendor: AsusTek Computer Inc.
                   physical id: d
                   bus info: usb@1:d
                   version: 1.00
                   serial: 9876543210
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=16mA speed=12Mbit/s
              *-usb:5
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: e
                   bus info: usb@1:e
                   version: 0.02
                   capabilities: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.8.0-53-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.08
                capabilities: usb-3.10
                configuration: driver=hub slots=9 speed=10000Mbit/s
              *-usb
                   description: Mass storage device
                   product: USB3.0
                   vendor: UDISK
                   physical id: 9
                   bus info: usb@2:9
                   version: a.00
                   serial: 09021000000000003874130617
                   capabilities: usb-3.00 scsi
                   configuration: driver=usb-storage maxpower=504mA speed=5000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 11
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: iomemory:600-5ff iomemory:600-5ff memory:6001118000-600111bfff memory:6001120000-6001120fff
        *-network
             description: Wireless interface
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             logical name: wlo1
             version: 11
             serial: 8c:55:4a:9a:f9:fc
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-53-generic firmware=55.d9698065.0 QuZ-a0-hr-b0-55.u ip=192.168.2.59 latency=0 link=yes multicast=yes wireless=IEEE 802.11
             resources: iomemory:600-5ff irq:16 memory:6001114000-6001117fff
        *-serial:0
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:27 memory:4010200000-4010200fff
        *-serial:1
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:40 memory:4010201000-4010201fff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: iomemory:600-5ff irq:142 memory:600111d000-600111dfff
        *-sata
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:126 memory:a1500000-a1501fff memory:a1503000-a15030ff ioport:4090(size=8) ioport:4080(size=4) ioport:4060(size=32) memory:a1502000-a15027ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 memory:a1400000-a14fffff
           *-storage
                description: Non-Volatile memory controller
                product: SSD 660P Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:a1400000-a1403fff
              *-nvme0
                   description: NVMe device
                   product: INTEL SSDPEKNW512G8
                   physical id: 0
                   logical name: /dev/nvme0
                   version: 004C
                   serial: BTNH104510S1512A
                   configuration: nqn=nqn.2021-01.com.intel:nvm-subsystem-sn-btnh104510s1512a state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
                      size: 476GiB (512GB)
                      capabilities: gpt-1.00 partitioned partitioned:gpt
                      configuration: guid=176110a6-54c5-4712-b23c-642a1ca0cb04 logicalsectorsize=512 sectorsize=512
                    *-volume:0 UNCLAIMED
                         description: Windows FAT volume
                         vendor: MSDOS5.0
                         physical id: 1
                         version: FAT32
                         serial: 40db-4f92
                         size: 255MiB
                         capacity: 259MiB
                         capabilities: boot fat initialized
                         configuration: FATs=2 filesystem=fat label=SYSTEM name=EFI system partition
                    *-volume:1
                         description: reserved partition
                         vendor: Windows
                         physical id: 2
                         logical name: /dev/nvme0n1p2
                         serial: 4cf00a5b-51d4-487e-84ee-477f3c1adb64
                         capacity: 127MiB
                         capabilities: nofs
                         configuration: name=Microsoft reserved partition
                    *-volume:2
                         description: Windows NTFS volume
                         vendor: Windows
                         physical id: 3
                         logical name: /dev/nvme0n1p3
                         version: 3.1
                         serial: 26db-9446
                         size: 494MiB
                         capacity: 499MiB
                         capabilities: boot precious ntfs initialized
                         configuration: clustersize=4096 created=2021-05-26 01:27:06 filesystem=ntfs label=Recovery name=Basic data partition state=clean
                    *-volume:3
                         description: Windows NTFS volume
                         vendor: Windows
                         physical id: 4
                         logical name: /dev/nvme0n1p4
                         version: 3.1
                         serial: 72659ec8-bc7d-1f41-b0c0-894f9300e984
                         size: 146GiB
                         capacity: 146GiB
                         capabilities: ntfs initialized
                         configuration: clustersize=4096 created=2021-05-26 01:27:10 filesystem=ntfs label=Windows name=Basic data partition state=clean
                    *-volume:4
                         description: Linux swap volume
                         vendor: Linux
                         physical id: 5
                         logical name: /dev/nvme0n1p5
                         version: 1
                         serial: 4fa68444-6c27-420c-9fb6-63ef49510a90
                         size: 3814MiB
                         capacity: 3814MiB
                         capabilities: nofs swap initialized
                         configuration: filesystem=swap pagesize=4095
                    *-volume:5
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 6
                         logical name: /dev/nvme0n1p6
                         logical name: /
                         version: 1.0
                         serial: 97853106-9dde-4bb7-ada7-25e282956f9f
                         size: 35GiB
                         capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                         configuration: created=2021-05-28 21:20:49 filesystem=ext4 lastmountpoint=/ modified=2021-05-29 00:44:52 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-05-29 00:44:52 state=mounted
                    *-volume:6
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 7
                         logical name: /dev/nvme0n1p7
                         logical name: /home
                         version: 1.0
                         serial: e225fd55-cbcb-404b-ac66-27db01e75f91
                         size: 78GiB
                         capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                         configuration: created=2021-05-28 21:50:25 filesystem=ext4 lastmountpoint=/home modified=2021-05-29 00:44:52 mount.fstype=ext4 mount.options=rw,relatime mounted=2021-05-29 00:44:52 state=mounted
                    *-volume:7
                         description: Windows NTFS volume
                         vendor: Windows
                         physical id: 8
                         logical name: /dev/nvme0n1p8
                         version: 3.1
                         serial: 84ad3978-5767-374a-986e-dbef139b798e
                         size: 212GiB
                         capacity: 212GiB
                         capabilities: ntfs initialized
                         configuration: clustersize=4096 created=2021-05-28 22:52:21 filesystem=ntfs label=data name=data state=clean
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:a1200000-a13fffff
           *-network
                description: Ethernet interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 03
                serial: f0:2f:74:db:de:f1
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=igc driverversion=0.0.1-k latency=0 link=no multicast=yes port=twisted pair
                resources: irq:19 memory:a1200000-a12fffff memory:a1300000-a1303fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 ioport:3000(size=4096) memory:a0800000-a11fffff ioport:4010000000(size=2097152)
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: iomemory:600-5ff iomemory:600-5ff irq:159 memory:6001110000-6001113fff memory:6001000000-60010fffff
        *-serial:2
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 11
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:600-5ff irq:16 memory:600111c000-600111c0ff ioport:efa0(size=32)
        *-serial:3 UNCLAIMED
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a1504000-a1504fff
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0501
          physical id: 2
          capabilities: pnp
          configuration: driver=serial
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
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
     *-scsi
          physical id: 9
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: PDI09_32G ACJ3.0
             vendor: UDISK
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 1.00
             size: 30GiB (32GB)
             capabilities: removable
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sda
                size: 30GiB (32GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=64414873
              *-volume
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 1
                   logical name: /dev/sda1
                   logical name: /media/makem/729E-8842
                   version: FAT32
                   serial: 729e-8842
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
makem@makem-pc:~$ 

```

---

