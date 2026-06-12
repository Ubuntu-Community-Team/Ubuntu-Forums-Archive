---
title: "CUPS server error when adding printer in 18.10"
date: 2018-11-05
forum: General Help
---

### Post by pastlife on 2018-11-05
I upgraded my system to 18.10 and I've been loving it, except now I cannot connect to my printer. It is a WirelessLAN connected printer and I dont have the option to connect to it via USB. When I was running 18.04 I had no issues, and when I upgraded I couldn't print (CUPS error that reads: *There was an error during the CUPS operation: 'server-error-internal-error'* ) so I removed the printer in settings, rebooted, and tried to add it again after I entered these commands: **sudo apt-get install cups --reinstall** then **sudo service cups restart .** I got the same error 

Being a total noob, I thought maybe this was a bug because the upgrade. So I did a clean install of 18.10 from a fresh download and I'm getting the same error. I have tried to manually find the drivers for my printer but none worked. Has anyone else had printer driver issues in 18.10? I really don't want to go back to 18.04 but man, I'm over here logging into my windows machine just to print. That is sooooo sad.
[B]
The printer is: HP-ENVY-5530 series[/B] and I dont know what version of cups Im running or how to display that output in the terminal

here is my lshw output if needed.
```

root@genesis-01:/home/pastlife# lshw
genesis-01                  
    description: Desktop Computer
    product: MS-7A72 (Default string)
    vendor: MSI
    version: 1.0
    serial: Default string
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=desktop family=Default string sku=Default string uuid=00000000-0000-0000-0000-309C239CA088
  *-core
       description: Motherboard
       product: B250 PC MATE (MS-7A72)
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: I216213113
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.60
          date: 11/17/2017
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: 2400 C16 Series
             vendor: 8502
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: 2400 C16 Series
             vendor: 8502
             physical id: 2
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          physical id: 42
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 43
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 44
          slot: L3 Cache
          size: 4MiB
          capacity: 4MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-7320 CPU @ 4.10GHz
          vendor: Intel Corp.
          physical id: 45
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-7320 CPU @ 4.10GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1086MHz
          capacity: 4100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp flush_l1d cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:dfe00000-dfefffff ioport:c0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Baffin [Radeon RX 550 640SP / RX 560/560X]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: cf
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=amdgpu latency=0
                resources: irq:131 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:dfe00000-dfe3ffff memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD/ATI]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:130 memory:dfe60000-dfe63fff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: latency=0
             resources: memory:dff4f000-dff4ffff
        *-usb
             description: USB controller
             product: 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:120 memory:dff30000-dff3ffff
        *-generic:1 UNCLAIMED
             description: Signal processing controller
             product: 200 Series PCH Thermal Subsystem


Thank you for your time :)
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:dff4e000-dff4efff
        *-communication
             description: Communication controller
             product: 200 Series PCH CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:128 memory:dff4d000-dff4dfff
        *-storage
             description: SATA controller
             product: 200 Series PCH SATA controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:126 memory:dff48000-dff49fff memory:dff4c000-dff4c0ff ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:dff4b000-dff4b7ff
        *-pci:1
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:dfd00000-dfdfffff
           *-usb
                description: USB controller
                product: ASMedia Technology Inc.
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:dfd00000-dfd07fff
        *-pci:2
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 200 Series PCH LPC Controller (B250)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: 200 Series/Z370 Chipset Family Power Management Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:dff44000-dff47fff
        *-multimedia
             description: Audio device
             product: 200 Series PCH HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:129 memory:dff40000-dff43fff memory:dff20000-dff2ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 200 Series/Z370 Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:dff4a000-dff4a0ff ioport:f000(size=32)
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 00
             serial: 30:9c:23:9c:a0:88
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.1.80 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:127 memory:dff00000-dff1ffff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000VN002-2EY1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SC60
             serial: Z9C3Z073
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=64a8e0a0-6710-4c5d-b095-76909153f225 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Linux swap volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: 8bffa32c-bf74-4c45-b98b-4fff187b598a
                size: 7626MiB
                capacity: 7627MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:1
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: 102b-1a14
                size: 478MiB
                capacity: 491MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                version: 1.0
                serial: df3b8cba-d6cc-4d85-8ff0-da2135954231
                size: 923GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2018-11-03 20:01:22 filesystem=ext4 lastmountpoint=/ modified=2018-11-05 11:22:41 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2018-11-05 11:22:44 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B1ST   j
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Cruzer Glide
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: 20051942621163130DB7
             size: 14GiB (15GB)
             capabilities: removable
             configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 14GiB (15GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=07d67448
              *-volume
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/pastlife/new
                   version: FAT32
                   serial: 4396-3779
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=new mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
root@genesis-01:/home/pastlife#
```

---

### Post by him610 on 2018-11-05
Cups is not the problem, only the symptom of the problem. Hplip should allow out of the box installation for HP printers. I believe hplip is part of each *buntu distribution. 
Did you download drivers for your printer from [https://developers.hp.com/hp-linux-imaging-and-printing]("https://developers.hp.com/hp-linux-imaging-and-printing")?

---

