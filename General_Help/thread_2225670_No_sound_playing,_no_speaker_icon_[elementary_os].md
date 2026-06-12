---
title: "No sound playing, no speaker icon [elementary os]"
date: 2014-05-22
forum: General Help
---

### Post by nfcristea on 2014-05-22
[COLOR=#000000][FONT=Arial]I am new to Linux but really love Elementary for its simplicity. After noticing that my sound was quite poor in Elementary, compared to Windows 8.1, I have tried updating the sound drivers. I ended up downloading one from [here]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2") but after a reboot, my sound icon was gone from the toolbar and no sound can be heard. In the setting > sound I see "Dummy Output" and running alsamixer says cannot open mixer: No such file or directory. I have Googled around without any success and many suggest sudo alsa force-reload but that returns[/FONT][/COLOR]
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
[COLOR=#000000][FONT=Arial]I have lost hope after posting in other places without any replies and I am hoping somebody here can help. I have uninstalled the driver I have previously downloaded from the link above (maybe there are pieces left behind?) and purged reinstalled both alsa-base and pulseaudio but I still can not see the sound icon or play sounds.

[B]lshw output:
[/B][/FONT][/COLOR]
description: Portable Computer
    product: Inspiron 3537 (Inspiron 3537)
    vendor: Winbond Electronics
    version: A07
    serial: 2FN1402
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=portable family=00 frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=Inspiron 3537 uuid=44454C4C-4600-104E-8031-B2C04F343032
  *-core
       description: Motherboard
       product: 03JPPR
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: .2FN1402.CN129664280036.
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A07
          date: 11/12/2013
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 759MHz
          capacity: 759MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: b
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 8
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5674QH0-YK0
             vendor: Samsung
             physical id: 0
             serial: 98D205AC
             slot: JDIMM1
             size: 2GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: NT4GC64C88B1NS-DI
             vendor: Nanya Technology
             physical id: 1
             serial: F85A1057
             slot: JDIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:61 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:4000(size=64)
        *-multimedia:0 UNCLAIMED
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:b0710000-b0713fff
        *-usb:0
             description: USB controller
             product: Lynx Point-LP USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:58 memory:b0700000-b070ffff
        *-communication UNCLAIMED
             description: Communication controller
             product: Lynx Point-LP HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:b0718000-b071801f
        *-multimedia:1 UNCLAIMED
             description: Audio device
             product: Lynx Point-LP HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:b0714000-b0717fff
        *-pci:0
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:56 ioport:3000(size=4096) memory:b0600000-b06fffff ioport:b0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 07
                serial: ec:f4:bb:87:45:0c
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:60 ioport:3000(size=256) memory:b0600000-b0600fff memory:b0400000-b0403fff
        *-pci:1
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:57 memory:b0500000-b05fffff ioport:9fb00000(size=1048576)
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 64:5a:04:ca:09:df
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.8.0-39-generic firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:b0500000-b057ffff memory:9fb00000-9fb0ffff
        *-usb:1
             description: USB controller
             product: Lynx Point-LP USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b071c000-b071c3ff
        *-isa
             description: ISA bridge
             product: Lynx Point-LP LPC Controller
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
             description: SATA controller
             product: Lynx Point-LP SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:59 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:b071b000-b071b7ff
        *-serial UNCLAIMED
             description: SMBus
             product: Lynx Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b0719000-b07190ff ioport:4040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54757
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: JE4O
             serial: J2140054KYR1XB
             size: 698GiB (750GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=0f7b0e6a-9fa4-449d-8fb3-524c80e127f4
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 0e9a-917c
                size: 495MiB
                capacity: 499MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: FAT32
                serial: 600d-e074
                size: 15MiB
                capacity: 39MiB
                capabilities: precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat name=Basic data partition
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: 7214-8f07
                size: 98MiB
                capacity: 127MiB
                capabilities: nofs ntfs initialized
                configuration: clustersize=4096 created=2014-04-26 20:59:47 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true name=Microsoft reserved partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: Windows NTFS volume
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: e012-cf26
                size: 460MiB
                capacity: 489MiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-02-07 18:33:16 filesystem=ntfs label=WINRETOOLS name=Basic data partition state=clean
           *-volume:4
                description: Windows NTFS volume
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: 8e282093-121f-2e48-901e-b0cc0d3175aa
                size: 201GiB
                capacity: 201GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-02-07 18:33:27 filesystem=ntfs label=OS name=Basic data partition state=clean
           *-volume:5
                description: Windows NTFS volume
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: 88bb-16a8
                size: 433MiB
                capacity: 449MiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-04-27 21:10:23 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: Windows NTFS volume
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /media/sda7
                version: 3.1
                serial: 3a09b668-4147-4c4a-8f39-e329be48fcbf
                size: 341GiB
                capacity: 341GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-04-26 00:17:41 filesystem=ntfs label=Media modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true name=Basic data partition resize_log_file=true state=mounted upgrade_on_mount=true
           *-volume:7
                description: Windows NTFS volume
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                version: 3.1
                serial: 70f2-defe
                size: 12GiB
                capacity: 12GiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-02-07 21:44:42 filesystem=ntfs label=PBR Image modified_by_chkdsk=true mounted_on_nt4=true name=Microsoft recovery partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:8
                description: EXT4 volume
                vendor: Linux
                physical id: 9
                bus info: scsi@0:0.0.0,9
                logical name: /dev/sda9
                logical name: /
                version: 1.0
                serial: a6c40c87-72a3-4600-a9f5-4e2164d727ad
                size: 135GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-04-28 17:36:17 filesystem=ext4 lastmountpoint=/ modified=2014-05-21 20:44:45 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-05-21 20:55:17 state=mounted
           *-volume:9
                description: Linux swap volume
                physical id: a
                bus info: scsi@0:0.0.0,10
                logical name: /dev/sda10
                version: 1
                serial: 3cf35bdb-523c-4c09-8f2d-bed23767416c
                size: 6023MiB
                capacity: 6024MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GU90N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: A100
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
     *-scsi:2
          physical id: 3
          bus info: usb@1:1.7
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=rts5139
        *-disk
             description: SCSI Disk
             product: xD/SD/M.S.
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-battery
       description: Lithium-Ion Battery
       product: DELL 4WY7C416
       vendor: SANYO
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 28000mWh
       configuration: voltage=14.8V
[COLOR=#000000][FONT=Arial][B]
lspci:

[/B][FONT=Consolas]00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)[/FONT][/FONT][/COLOR]
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)[COLOR=#000000][FONT=Arial]
Any help is greatly appreciated. Many thanks in advance[/FONT][/COLOR]

---

