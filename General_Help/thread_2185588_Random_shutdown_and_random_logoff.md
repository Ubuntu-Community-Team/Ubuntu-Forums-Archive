---
title: "Random shutdown and random logoff?"
date: 2013-11-03
forum: General Help
---

### Post by Mopar1973Man on 2013-11-03
I've got one that's got me stumped. 

I've got a random just powering off no warning or nothing and power completely off and pause for up to 5-10 seconds and then power back up. Or the other version is being booted back to login screen. This is completely random it might not do it for a few days and then do it for several times then quit for several days or weeks.

Done a memory test and passed.
Double checked all sockets and connections all good.
Conky Panel is up and never have a temp or voltage issue.

Hardware list below.

```

    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: M3A
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1206
          date: 06/11/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2700MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM_A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM_B1
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM_A2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM_B2
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RX780/RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fa000000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8500 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:e800(size=128) memory:feae0000-feafffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port C)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: Attansic L1 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: 00:1e:8c:6a:e6:38
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=192.168.254.39 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:42 memory:febc0000-febfffff memory:feba0000-febbffff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:d000(size=8) ioport:c000(size=4) ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=16) memory:f9fff800-f9fffbff
        *-usb:0
             description: USB controller
             product: SB600 USB (OHCI0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f9ffe000-f9ffefff
        *-usb:1
             description: USB controller
             product: SB600 USB (OHCI1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f9ffd000-f9ffdfff
        *-usb:2
             description: USB controller
             product: SB600 USB (OHCI2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffc000-f9ffcfff
        *-usb:3
             description: USB controller
             product: SB600 USB (OHCI3)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f9ffb000-f9ffbfff
        *-usb:4
             description: USB controller
             product: SB600 USB (OHCI4)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffa000-f9ffafff
        *-usb:5
             description: USB controller
             product: SB600 USB Controller (EHCI)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f9fff000-f9fff0ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f9ff4000-f9ff7fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EARX-00N
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 51.0
             serial: WD-WCC0S0214009
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000a0750
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 502f606e-0806-431f-a539-2da55ca99cb5
                size: 76GiB
                capacity: 76GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-03-13 11:04:43 filesystem=ext4 label=linux os lastmountpoint=/ modified=2013-04-15 10:35:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-11-03 08:07:16 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 854GiB
                capacity: 854GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5GiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /media/music
                   capacity: 151GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /media/pictures
                   capacity: 151GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   logical name: /media/website
                   capacity: 151GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   logical name: /media/downloads
                   capacity: 151GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:5
                   description: Linux filesystem partition
                   physical id: a
                   logical name: /dev/sda10
                   logical name: /media/video
                   capacity: 151GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:6
                   description: Linux filesystem partition
                   physical id: b
                   logical name: /dev/sda11
                   logical name: /home
                   capacity: 92GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST31500541AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: CC34
             serial: 9XW01XRR
             size: 1397GiB (1500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=69576504-6c68-4f56-899c-c0bc4cf1d215
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Backups
                version: 1.0
                serial: 8433bef0-c5ea-4b0f-8125-341f9ac0066c
                size: 1397GiB
                capacity: 1397GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-03 15:39:16 filesystem=ext4 label=Backups lastmountpoint=/media/Backups modified=2013-11-03 08:07:16 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-11-03 08:07:16 state=mounted
     *-scsi:2
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: iHAS124   B
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: AL0S
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:3
          physical id: 5
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: MS/MS-Pro
             vendor: Generic-
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdf
             version: 1.03
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf

```

---

### Post by tgalati4 on 2013-11-03
Look through the log files:

```
more /var/log/syslog
more /var/log/syslog.1
```

How old is the computer?  It could be the power supply causing a kernel panic.  When you don't get clear or consistent log messages or errors, I would spend some time on the hardware.  What are the SMART parameters on the disk drive?  It could also be a failing motherboard--an internal copper trace has corroded or, more likely, delamination of a support chip.

---

### Post by Mopar1973Man on 2013-11-03
Oh boy the computer is quite old at least 7-9 years old. I really haven't found any supporting errors or kernel panic listed in the logs. Both drives show healthy on the disk utility no bad sectors at all.

---

### Post by tgalati4 on 2013-11-03
Put a voltmeter on the power supply and check the power rails.  You might be able to see the voltages in BIOS under PC Health Management.

---

### Post by Mopar1973Man on 2013-11-03
```

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.09 V  (min =  +0.85 V, max =  +1.60 V)
+12V Voltage:      +11.90 V  (min = +10.20 V, max = +13.80 V)
+5V Voltage:        +4.95 V  (min =  +4.50 V, max =  +5.50 V)
+3.3V Voltage:      +3.31 V  (min =  +2.97 V, max =  +3.63 V)
CPU FAN Speed:     2257 RPM  (min =  800 RPM)
Chassis FAN Speed: 2576 RPM  (min =  800 RPM)
Power Fan Speed:   2528 RPM  (min =  800 RPM)
CPU Temperature:   +125.6°F  (high = +149.0°F, crit = +203.0°F)
MB Temperature:     +98.6°F  (high = +113.0°F, crit = +203.0°F)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +93.2°F  
Core0 Temp:   +86.0°F  
Core1 Temp:   +87.8°F  
Core1 Temp:   +86.0°F  

```

Strange is it did it twice this morning then quit again been stable all day long and been working with the machine as well. Just strange... I'll have to run down to the shop and get the DVM and verify the power voltage beyond the block I provided. Note: I'm using Cool and Quiet on the BIOS. Huge savings for the house battery system.

---

### Post by Yellow Pasque on 2013-11-03
If this happens under load, then monitor temperatures. Finding a few hours to run Memtest wouldn't hurt either...

---

