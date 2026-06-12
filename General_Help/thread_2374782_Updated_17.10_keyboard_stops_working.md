---
title: "Updated 17.10 keyboard stops working"
date: 2017-10-19
forum: General Help
---

### Post by wildmanne39 on 2017-10-19
My keyboard is acting like the insert button has been pressed then it completely stops working and the only way to get it to work again is to reboot.

This is on my laptop with amd radeon 6 graphics.

---

### Post by wildmanne39 on 2017-10-20
*Thread moved to **General Help for better a better fit **.*

---

### Post by sudodus on 2017-10-20
- Please tell us about the computer (and its hardware, not only the graphics).

- Is it a fresh installation or an upgraded system?

- Is a live session affected (in the same laptop)?

---

### Post by wildmanne39 on 2017-10-20
Hi, my hardware:
```
larry@larry-HP-Pavilion-Notebook:~$ sudo lshw
[sudo] password for larry: 
larry-hp-pavilion-notebook  
    description: Notebook
    product: HP Pavilion Notebook (N9E13UA#ABA)
    vendor: HP
    version: Chassis Version
    serial: xxxxxxxxxx
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV sku=N9E13UA#ABA uuid=35434436-3234-4239-5336-EC8EB5432E26
  *-core
       description: Motherboard
       product: 80B0
       vendor: HP
       physical id: 0
       version: 81.32
       serial: PFFVP018J301DU
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F.45
          date: 04/28/2017
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cache:0
          description: L1 cache
          physical id: d
          slot: L1 CACHE
          size: 320KiB
          capacity: 320KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: e
          slot: L2 CACHE
          size: 2MiB
          capacity: 2MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1866 MHz (0.5 ns)
             product: 8KTF51264HZ-1G9P1
             vendor: Micron
             physical id: 0
             serial: 12B0AAAA
             slot: Bottom-Slot 1 (left)
             size: 4GiB
             width: 64 bits
             clock: 1866MHz (0.5ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1866 MHz (0.5 ns)
             product: 8KTF51264HZ-1G9P1
             vendor: Micron
             physical id: 1
             serial: 12B0AACE
             slot: Bottom-Slot 2 (right)
             size: 4GiB
             width: 64 bits
             clock: 1866MHz (0.5ns)
     *-cpu
          description: CPU
          product: AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G
          vendor: Advanced Micro Devices [AMD]
          physical id: 21
          bus info: cpu@0
          version: AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G
          slot: P0
          size: 1458MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload overflow_recov cpufreq
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
        *-generic:0 UNCLAIMED
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
        *-display
             description: VGA compatible controller
             product: Carrizo
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: c5
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=amdgpu latency=0
             resources: irq:49 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Kabini HDMI/DP Audio
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:53 memory:feb64000-feb67fff
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:fea00000-feafffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:37 memory:fea00000-fea00fff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:e000(size=4096) memory:fe900000-fe9fffff
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eno1
                version: 07
                serial: ec:8e:b5:43:2e:26
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:39 ioport:e000(size=256) memory:fe914000-fe914fff memory:fe910000-fe913fff memory:fe900000-fe90ffff
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:d000(size=4096) memory:fe800000-fe8fffff
           *-network
                description: Wireless interface
                product: RTL8188EE Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlo1
                version: 01
                serial: 40:49:0f:39:0a:bb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8188ee driverversion=4.13.0-16-generic firmware=N/A ip=192.168.0.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:51 ioport:d000(size=256) memory:fe800000-fe803fff
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:1000(size=4096) memory:f0900000-f0afffff ioport:f0b00000(size=2097152)
        *-generic:1 UNCLAIMED
             description: Encryption controller
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msix ht pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0800000-f081ffff memory:fe700000-fe7fffff memory:feb6f000-feb6ffff memory:feb6a000-feb6bfff
        *-multimedia:1
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:54 memory:feb60000-feb63fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:feb68000-feb69fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.13.0-16-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb
                   description: Video
                   product: HP Truevision HD
                   vendor: Generic
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.03
                   serial: DETGB019I193AO
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.13.0-16-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.13
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:40 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb6d000-feb6d3ff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:feb6c000-feb6c0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Advanced Micro Devices, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 4a
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:09.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS541010A9
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A7G0
             serial: JD1090DP0R89ST
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=77800fa7-3993-4cd0-8899-183ddcce280b logicalsectorsize=512 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: 52a9-0668
                size: 255MiB
                capacity: 259MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=SYSTEM name=EFI system partition
           *-volume:1
                description: reserved partition
                vendor: Windows
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                serial: 46c73fad-e12c-4d29-9634-f6db1a3edb4d
                capacity: 15MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: 58287762-c8b5-024c-b0e2-f0a708e649ce
                size: 457GiB
                capacity: 457GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2015-12-23 04:38:36 filesystem=ntfs label=Windows name=Basic data partition state=clean
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: deab-c5f9
                size: 1720MiB
                capacity: 1739MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2017-09-25 18:33:19 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 1.0
                serial: a52dcd1f-63d0-4854-b7ba-3a2a96eef74d
                size: 264GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2016-12-10 17:49:44 filesystem=ext4 lastmountpoint=/home modified=2017-04-26 00:32:42 mounted=2017-04-26 00:32:42 name=Basic data partition state=clean
           *-volume:5
                description: EXT4 volume
                vendor: Linux
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 1.0
                serial: f8bd148a-710f-41e2-8c18-acc5da67ef59
                size: 93GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2017-04-24 18:16:30 filesystem=ext4 modified=2017-04-25 17:35:36 mounted=2017-04-25 17:35:36 state=clean
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /
                version: 1.0
                serial: 6dffc536-f5fd-4e21-a77c-b87e3a49b72a
                size: 46GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2017-04-25 16:49:36 filesystem=ext4 lastmountpoint=/ modified=2017-10-20 13:34:30 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-10-20 13:34:38 state=mounted
           *-volume:7
                description: EXT4 volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                version: 1.0
                serial: ca6038ed-8470-4b60-95c8-20bb8f88e4ef
                size: 37GiB
                capacity: 46GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2016-12-10 17:50:01 filesystem=ext4 lastmountpoint=/ modified=2017-04-26 00:32:17 mounted=2017-04-26 00:32:35 state=clean
           *-volume:8
                description: Linux swap volume
                vendor: Linux
                physical id: 9
                bus info: scsi@0:0.0.0,9
                logical name: /dev/sda9
                version: 1
                serial: e8a9da11-ac87-4725-a70a-f492dd7251a0
                size: 1907MiB
                capacity: 1907MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:9
                description: Windows NTFS volume
                vendor: Windows
                physical id: a
                bus info: scsi@0:0.0.0,10
                logical name: /dev/sda10
                version: 3.1
                serial: a04a-db64
                size: 832MiB
                capacity: 837MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-12-07 21:36:42 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:10
                description: Windows NTFS volume
                vendor: Windows
                physical id: b
                bus info: scsi@0:0.0.0,11
                logical name: /dev/sda11
                version: 3.1
                serial: d01c3273-b0fc-4742-a57f-4541f9d492cc
                size: 18GiB
                capacity: 18GiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-06-20 21:45:52 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW GUD1N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: MD00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: KI04041
       vendor: 131-22-6E
       physical id: 1
       slot: Primary
       capacity: 41610mWh
       configuration: voltage=14.6V
larry@larry-HP-Pavilion-Notebook:~$ 

```
I upgraded from the dev version, as long as I do not put pressure on the laptop it seems to be okay but once it acts up I have to get my fingers or wrists off the laptop quick or I have to reboot, this does not happen with other versions of Ubuntu, it is like the touch pad is sensitive but I tried to adjust it and that did not make any difference.

I do not have a live version and I really do not plan to create one if I do have too. 

This happens with x.org or wayland.

It is very much like the insert button is on too but clicking it does not help, when typing the it high light the text and replace it or start typing in a new place instead of where I had the cursor.

Thanks for your reply.

---

### Post by #&amp;thj^% on 2017-10-20
> **wildmanne39 said:**
> My keyboard is acting like the insert button has been pressed then it completely stops working and the only way to get it to work again is to reboot.

This is on my laptop with amd radeon 6 graphics.

Howdy Wild Man...is this installed\
```
apt policy xserver-xorg-input-all
```
I've seen this happen without clean installs

---

### Post by wildmanne39 on 2017-10-20
I should be using wayland at the moment I think, I am logged in to just Ubuntu.
```
xserver-xorg-input-all:
  Installed: 1:7.7+19ubuntu3
  Candidate: 1:7.7+19ubuntu3
  Version table:
 *** 1:7.7+19ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status

```

Hi 1fallen, glad you are on today!

---

### Post by #&amp;thj^% on 2017-10-20
> **wildmanne39 said:**
> I should be using wayland at the moment I think, I am logged in to just Ubuntu.
```
xserver-xorg-input-all:
  Installed: 1:7.7+19ubuntu3
  Candidate: 1:7.7+19ubuntu3
  Version table:
 *** 1:7.7+19ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status

```

Hi 1fallen, glad you are on today!
Good to see you!;)
This also happened to me earlier in the cycle (17.10)
Trying to find my notes on how I fixed it.(Will report back here when i find it)

---

### Post by wildmanne39 on 2017-10-20
Thanks 1fallen!:)

---

### Post by sudodus on 2017-10-21
Good to see you again @1fallen :-)

---

### Post by Bashing-om on 2017-10-21
sudodus: Hello -

See wildman's Xorg file:
[https://pastebin.com/zGsn3pJi](https://pastebin.com/zGsn3pJi)
in respect to the keyboard activity and it's " device removed " .

Question: of what value is an Xorg file in a wayland environment ?

[INDENT]sometimes I do wonder[/INDENT]

---

### Post by wildmanne39 on 2017-10-21
Thanks for posting the the link to pastebin bashin-om, it has been a crazy busy night.

I ran the command to see if wayland is running and it is.

---

### Post by sudodus on 2017-10-21
> **Bashing-om said:**
> sudodus: Hello -

See wildman's Xorg file:
[https://pastebin.com/zGsn3pJi](https://pastebin.com/zGsn3pJi)
in respect to the keyboard activity and it's " device removed " .

Question: of what value is an Xorg file in a wayland environment ?

[INDENT]sometimes I do wonder[/INDENT]

Hello @Bashing-om :-)

1. I must admit, that I am not good at reading log files. Yes, I could find the instances of "device removed" but don't know if it would affect the problems of this thread.

2. There is an option to run the new Ubuntu with Xorg instead of Wayland. That could be a reason why the Xorg file is there. (I have no idea if an Xorg file is used by Wayland, probably not, but I would not be sure.)

---

### Post by wildmanne39 on 2017-10-21
sudodus thanks for taking a look at this issue.

---

### Post by #&amp;thj^% on 2017-10-21
> **Bashing-om said:**
> 
Question: of what value is an Xorg file in a wayland environment ?

[INDENT]sometimes I do wonder[/INDENT]
Hiya Bashing-om :D in regards to Wayland uses libinput, and configuration should be handled by the compositor.
Also have a look at this: [https://wayland.freedesktop.org/libinput/doc/latest/faq.html](https://wayland.freedesktop.org/libinput/doc/latest/faq.html)
Belive it or not mine was caused by an incorrect pressure threshold range on my Lenovo Lappy

See this: [https://wayland.freedesktop.org/libinput/doc/latest/faq.html](https://wayland.freedesktop.org/libinput/doc/latest/faq.html)

Touchpad pressure-based touch detection 
[https://wayland.freedesktop.org/libinput/doc/latest/touchpad_pressure.html](https://wayland.freedesktop.org/libinput/doc/latest/touchpad_pressure.html)
@Wild Man sorry it took so long to get back to you.
Keep this thread updated if you would.
Best Regards

---

### Post by wildmanne39 on 2017-10-21
> **1fallen said:**
> Hiya Bashing-om :D in regards to Wayland uses libinput, and configuration should be handled by the compositor.
Also have a look at this: [https://wayland.freedesktop.org/libinput/doc/latest/faq.html](https://wayland.freedesktop.org/libinput/doc/latest/faq.html)
Belive it or not mine was caused by an incorrect pressure threshold range on my Lenovo Lappy

See this: [https://wayland.freedesktop.org/libinput/doc/latest/faq.html](https://wayland.freedesktop.org/libinput/doc/latest/faq.html)

Touchpad pressure-based touch detection 
[https://wayland.freedesktop.org/libinput/doc/latest/touchpad_pressure.html](https://wayland.freedesktop.org/libinput/doc/latest/touchpad_pressure.html)
@Wild Man sorry it took so long to get back to you.
Keep this thread updated if you would.
Best Regards
Thanks 1fallen I do think that is my issue as well, it looks complicated but I will just take it one step at a time.

Glad you are back today!

---

### Post by wildmanne39 on 2017-10-21
```
sudo libinput measure touchpad-pressure
```
says command not found.

---

### Post by Bashing-om on 2017-10-21
@1fallen - Great info

Thanks for sharing

All for 1 and one for all

---

### Post by #&amp;thj^% on 2017-10-21
> **wildmanne39 said:**
> ```
sudo libinput measure touchpad-pressure
```
says command not found.
That's what mine reported the first time also ;(
I think I had to install the "evemu" package providing the ```evemu-record``` tool. 
Then to get it to show up:
```
sudo evemu-record > touchpad-pressure.txt
```


> **Bashing-om said:**
> @1fallen - Great info

Thanks for sharing

All for 1 and one for all
Welcome...But that's how we roll here>>>Sharing is Caring:D

---

### Post by wildmanne39 on 2017-10-21
The evemu package is not found, I tried to enable repositories to see if that will help but so far each method I have tried does not work with 17.10.

---

### Post by Bashing-om on 2017-10-21
@wildman:

see:
[https://packages.ubuntu.com/search?keywords=libinput&searchon=names&suite=artful&section=all](https://packages.ubuntu.com/search?keywords=libinput&searchon=names&suite=artful&section=all)
the package is libinput-bin .
```

apt list libinput-bin

```

Maybe yes

---

### Post by #&amp;thj^% on 2017-10-21
> **wildmanne39 said:**
> The evemu package is not found, I tried to enable repositories to see if that will help but so far each method I have tried does not work with 17.10.

It is in Proposed.
> -First, install the "evemu" package providing the ```evemu-record``` tool.
-Run ```evemu-record``` as root (without arguments) to see a list of devices
-and select the touchpad device. Pipe the actual output of the tool into a
-file for later analysis. For example:
+Use the ```libinput measure touchpad-pressure``` tool provided by libinput.
+This tool will search for your touchpad device and print some pressure
+statistics, including whether a touch is/was considered logically down.
+Example output of the tool is below:
Also would you show me the output of:
```
cat /sys/class/input/event*/device/name
```
Yep this is a fun one...LOL

---

### Post by wildmanne39 on 2017-10-21
Here it is:
```
cat /sys/class/input/event*/device/name
Power Button
HDA ATI HDMI HDMI/DP,pcm=3
HD-Audio Generic Mic
HD-Audio Generic Headphone
Lid Switch
Power Button
AT Translated Set 2 keyboard
Video Bus
SynPS/2 Synaptics TouchPad
HP Wireless hotkeys
ST LIS3LV02DL Accelerometer
HP WMI hotkeys
HP Truevision HD: HP Truevision

```

---

### Post by #&amp;thj^% on 2017-10-21
Ah Ha Seen some oddities with this "ST LIS3LV02DL Accelerometer" 
Try Blacklisting first just to see **hp_accel module**:
```
sudo modprobe -r hp_accel

```
If you don't want your system to load the module at every boot, simply blacklist it adding the following line to
/etc/modprobe.d/blacklist.conf:
```

blacklist hp_accel
```

You probably already know this but I mention it anyway for future visitors.
The accelerometer detects when you drop your laptop, and quickly stops the HDD to minimize damage. That probably doesn't work on Linux anyway.
Fingers Crossed

---

### Post by wildmanne39 on 2017-10-21
I blacklisted the module, so I will report back after testing.

Thanks

---

### Post by wildmanne39 on 2017-10-21
Blacklisting seems to have fixed it.

Thanks 1fallen.

---

### Post by #&amp;thj^% on 2017-10-21
Woot Woot!  Hope that fixed it.:)

---

### Post by wildmanne39 on 2017-10-23
This does seem to fix the issue but I had to unblacklist it because my monitor issue got really bad where it was going blank before I could even log in.

Thanks 1fallen for the effort!

---

### Post by #&amp;thj^% on 2017-10-23
> **wildmanne39 said:**
> This does seem to fix the issue but I had to unblacklist it because my monitor issue got really bad where it was going blank before I could even log in.

Thanks 1fallen for the effort!

I would file a bug against this. I was thinking it might have side effects.
Not seeing this issue with Arch and  "ST LIS3LV02DL Accelerometer"  but not really helpful here. :(

---

### Post by wildmanne39 on 2017-10-27
An update, I had to switch to xserver for graphic card reasons and this issue is still causing trouble with it too.

---

### Post by sudodus on 2017-10-27
If you have time and energy enough, maybe you can check if this keyboard problem affects any of the following systems:

- a live session booted from an Ubuntu 16.04.1 LTS pendrive

- a live session booted from an Ubuntu 16.04.3 LTS pendrive

- an installed system booted from an updated & upgraded Ubuntu 16.04.1 LTS system (with the xenial kernel)

- an installed system booted from an updated & upgraded Ubuntu 16.04.3 LTS system (with the zesty kernel)

What I am getting at is, if it depends on the kernel and its drivers, or if it depends on some other program package, that might be updated & upgraded also in the LTS versions. (I would suspect, that it depends of the kernel and its drivers.)

---

### Post by wildmanne39 on 2017-10-28
I gave each of these methods a try but I am using a amd radeon 6 graphics card and I could not do proper testing the screen either went blank on boot or upon entering the desktop, 17.10 is the first version of Ubuntu that I have been able to run on it since I bought it a year ago until now I have used Ubuntu in a vm and it did not have this issue on 16.04 but then again it was using vb's drivers.

While I was typing this post I hit the print screen key and it made the keyboard stop typing, I clicked a few random keys like kijd and it shut the computer off immediately.

Thanks for your post and suggestions.

---

