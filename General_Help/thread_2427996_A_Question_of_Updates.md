---
title: "A Question of Updates"
date: 2019-09-28
forum: General Help
---

### Post by klyntone on 2019-09-28
Recently an update put me in a login loop.

I spent a few hours trying to fix it. (chown .Xauth .ICEauth, update display drivers, purge reinstall gnome, change gdm3 to lightdm, disabled extentions, upgaded to 19 and other solutions found with searching)

Eventually i restored to a clonezilla backup from 2 months ago.

In this back up some old issues are presenting, slow restart time, video playback gets blocky after long periods, keyboard backlight hotkeys dont work, these had been fixed by th updates preceeding th one that caused a login loop.

If i was to update my **current Ubuntu 18.04.2 LTS** now, would i be getting th update that resulted in me having th login loop;

Or would it be th update from 8 weeks ago followed by th one from 6 weeks ago and then th on from 4 weeks ago so i can resolve those few issues and then stop updating before th updated that caused th login loop?

Hope that makes sense.

Thanks in advance.

---

### Post by Autodave on 2019-09-28
I don't know if this will help anyone else to answer your question, but please give us some info on your machine.

---

### Post by klyntone on 2019-09-28
Ok, does that affect how Ubuntu updates work, do some machines get updates in order and other machines get an acumulation of all th updates.

I wish i knew th words for th different types of updates.

Do you have to get update 1 before you can get update 2 which will alow you to get update 3, OR does update 3 contain update 1 and update 2, does that make more sense?

Anyway Basic info:
ASUS VivoBook Dual Boot Win & Ubuntu
RAM 7.7 GiB
CPU Intel® Core&#8482; i7-8550U CPU @ 1.80GHz × 8
Graphics Intel® UHD Graphics 620 (Kabylake GT2)
Gnome 3.28.2
OS 64-bit
SSD 120 GB
Ubuntu Partition 50 GB

Detailed info:
```
:~$ sudo lshw
                
    description: Notebook
    product: VivoBook S15 X530UA
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: JAN0CX08E217434
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=VivoBook S uuid=38A5B32B-9DE1-46E3-AFC6-8B1F74B167AB
  *-core
       description: Motherboard
       product: X530UA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: QCCXKJ00H83900033
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: X530UA.305
          date: 05/21/2019
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: HMA81GS6AFR8N-UH
             vendor: SK Hynix
             physical id: 2
             serial: C02ECBEF
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:3
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          physical id: f
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 10
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 11
          slot: L3 Cache
          size: 8MiB
          capacity: 8MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: 12
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2146MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: UHD Graphics 620
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:128 memory:ee000000-eeffffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 08
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:ef120000-ef127fff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:124 memory:ef110000-ef11ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.18.0-25-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.18
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: HighSpeed Hub
                   vendor: NEC Corp.
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Generic USB device
                      product: eHome Infrared Transceiver
                      vendor: Philips
                      physical id: 2
                      bus info: usb@1:3.2
                      version: 0.00
                      serial: PH00Q8oH
                      capabilities: usb-1.10
                      configuration: driver=mceusb maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Keyboard
                      product: Dell USB Keyboard
                      vendor: Dell
                      physical id: 3
                      bus info: usb@1:3.3
                      version: 2.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=70mA speed=2Mbit/s
                 *-usb:2
                      description: Mouse
                      product: USB Optical Mouse
                      vendor: Primax Electronics, Ltd
                      physical id: 4
                      bus info: usb@1:3.4
                      version: 2.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Video
                   product: USB2.0 HD UVC WebCam
                   vendor: Azurewave
                   physical id: 6
                   bus info: usb@1:6
                   version: 18.52
                   serial: 0x0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.10
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.18.0-25-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.18
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
              *-usb
                   description: Mass storage device
                   product: Expansion Desk
                   vendor: Seagate
                   physical id: 1
                   bus info: usb@2:1
                   logical name: scsi3
                   version: 1.00
                   serial: NA4M970B
                   capabilities: usb-3.00 scsi
                   configuration: driver=uas maxpower=144mA speed=5000Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Expansion Desk
                      vendor: Seagate
                      physical id: 0.0.0
                      bus info: scsi@3:0.0.0
                      logical name: /dev/sda
                      version: 0712
                      serial: NA4M970B
                      size: 1863GiB (2TB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=6 logicalsectorsize=4096 sectorsize=4096 signature=90a4f1bb
                    *-volume UNCLAIMED
                         description: HPFS/NTFS partition
                         physical id: 1
                         bus info: scsi@3:0.0.0,1
                         capacity: 214GiB
                         capabilities: primary bootable
        *-generic:1
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:ef13a000-ef13afff
        *-generic:2
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #0
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:ef139000-ef139fff
        *-generic:3
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #1
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:ef138000-ef138fff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:126 memory:ef137000-ef137fff
        *-storage
             description: SATA controller
             product: Sunrise Point-LP SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:125 memory:ef130000-ef131fff memory:ef136000-ef1360ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:ef135000-ef1357ff
        *-pci:0
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:2000(size=4096) memory:a0000000-a01fffff ioport:a0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:ef000000-ef0fffff
           *-network
                description: Wireless interface
                product: Wireless 8265 / 8275
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 78
                serial: 00:bb:60:86:62:da
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.18.0-25-generic firmware=36.9f0a2d68.0 ip=192.168.1.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:127 memory:ef000000-ef001fff
        *-generic:4
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO UART Controller #0
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:20 memory:ef134000-ef134fff
        *-generic:5
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO SPI Controller #0
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:22 memory:ef133000-ef133fff
        *-isa
             description: ISA bridge
             product: Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: latency=0
             resources: memory:ef12c000-ef12ffff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:130 memory:ef128000-ef12bfff memory:ef100000-ef10ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:ef132000-ef1320ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000LM007-1R81
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb
             version: SDM3
             serial: WDZ7KXXN
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=d1e1719a-20b5-4dd1-8fcb-e4ddad5e7449 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/as-vo/INT-DATA
                version: 3.1
                serial: 1e451b30-c438-df43-88ae-85bc295cce8d
                size: 1763GiB
                capacity: 1763GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-10-25 08:16:16 filesystem=ntfs label=INT-DATA modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true name=Basic data partition resize_log_file=true state=mounted upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                vendor: Windows
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: 305c0446-1437-5746-a060-c18aebab17f4
                size: 99GiB
                capacity: 99GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2019-07-04 22:47:07 filesystem=ntfs label=INT-BUP modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SanDisk SD9SN8W1
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdc
             version: 3002
             serial: 180149420787
             size: 119GiB (128GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=6f5ca59c-05a1-4127-b574-05494249ced4 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdc1
                logical name: /boot/efi
                version: FAT32
                serial: 8e3f-f546
                size: 255MiB
                capacity: 259MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=SYSTEM mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:1
                description: reserved partition
                vendor: Windows
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdc2
                serial: 03c4a1a5-252e-4f1c-ae58-61ebc730aabc
                capacity: 15MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sdc3
                version: 3.1
                serial: cc236699-0596-ec42-a95b-5c8b97471838
                size: 71GiB
                capacity: 71GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-10-25 08:05:13 filesystem=ntfs label=OS name=Basic data partition state=clean
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sdc4
                version: 3.1
                serial: 3a50-9111
                size: 775MiB
                capacity: 799MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2018-10-25 09:10:03 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@1:0.0.0,5
                logical name: /dev/sdc5
                logical name: /
                version: 1.0
                serial: 58556fee-919d-4fd5-ba34-9ba976230ea1
                size: 46GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-06-09 06:37:50 filesystem=ext4 lastmountpoint=/ modified=2019-09-29 03:57:07 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-09-28 17:57:08 state=mounted
```

---

### Post by Dennis N on 2019-09-28
> If i was to update my current Ubuntu 18.04.2 LTS now, would i be getting th update that resulted in me having th login loop;

Upgrading to 19.04 using "Software Updater" will get you the latest available versions of all packages from the 19.04 repositories. Could be more recent than what you had last time.

---

### Post by Impavidus on 2019-09-29
> **klyntone said:**
> 
Do you have to get update 1 before you can get update 2 which will alow you to get update 3, OR does update 3 contain update 1 and update 2, does that make more sense?

If update 1, 2 and 3 are all to the same package, update 3 contains update 1 and 2 (unless update 2 was to undo update 1, which sometimes happens). The updates you get contain the new versions of the packages, not the changes relative to the previous version. And once update 2 has been released, you can no longer get update 1 to the same package separately using the normal channels. Updates to unrelated packages can be installed in any order you like.

So, if your problem was indeed caused by an upgrade (which rarely produce a login loop, with login failing and returning you to the login screen, but it's possible), you could narrow it down by upgrading the various packages until you find which one causes the issue. Do you remember the last update before the issue started? Do you still have the log files? But ultimately, the goal is to install all updates and to find out how you can do so without causing your login loop.

Also consider the possibility that the login loop wasn't caused by the upgrade, but happened for unrelated reasons.

---

### Post by klyntone on 2019-09-29
> **Impavidus said:**
> If update 1, 2 and 3 are all to the same package, update 3 contains update 1 and 2 (unless update 2 was to undo update 1, which sometimes happens). The updates you get contain the new versions of the packages, not the changes relative to the previous version. And once update 2 has been released, you can no longer get update 1 to the same package separately using the normal channels. Updates to unrelated packages can be installed in any order you like.

Thank you for the explanation and your follow up comments, it will help me as i consider how to move forward, much appreciated.

---

