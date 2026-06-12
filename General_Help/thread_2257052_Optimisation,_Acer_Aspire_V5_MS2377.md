---
title: "Optimisation, Acer Aspire V5 MS2377"
date: 2014-12-16
forum: General Help
---

### Post by oli.kerr on 2014-12-16
I bought my second hand laptop - Acer Aspire V5 MS2377 - around a month ago and after I got far too frustrated with the Windows 8.1 OS with its slow start up speeds and Acer's own software truly clogging up the system I decided to dual boot ubuntu 14.04. Unfortunately the Ubuntu OS isn't running as seamlessly as I'm used to. Firefox can lag, VLC is jumpy, and apps take an age to load. Here my my laptop specs (surely proficient to run Ubuntu 14.04):

Processor AMD A4-1250 APU
ROM        500Gb
RAM        2Gb

I think the main problem could be the extensive partitioning used to set up my dual boot:

```
oli@Extreme-Mk2:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for oli: 
NAME   FSTYPE   SIZE MOUNTPOINT      LABEL
sda           465,8G                 
&#9500;&#9472;sda1 ntfs     400M                 Recovery
&#9500;&#9472;sda2 vfat     300M /boot/efi       ESP
&#9500;&#9472;sda3          128M                 
&#9500;&#9472;sda4 ntfs   227,6G /media/oli/Acer Acer
&#9500;&#9472;sda5 ntfs    16,3G                 Push Button Reset
&#9500;&#9472;sda6 ext4    46,6G /               
&#9500;&#9472;sda7 ext4   167,1G /home           
&#9492;&#9472;sda8 swap     7,5G [SWAP]    

```

Suggestions? Save my recovery partition for windows 8.1 on a USB stick and reinstall Ubuntu as my only OS?

Thanks in advance

---

### Post by lisati on 2014-12-16
Making a copy of Windows recovery partitions is always a good idea. Many computers these days come with software that can assist in this task. Now to blow the cobwebs off my memory and figure out where I put the recovery disks I made for my machines! :D

---

### Post by oli.kerr on 2014-12-17
So you agree the excessive partitioning is the cause of slowing my OS?

---

### Post by mörgæs on 2014-12-17
No, a hard disk is not slower because you have a number of Windows partitions next to Ubuntu. 

If we are going to look at performance please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by oli.kerr on 2014-12-18
Thanks for your reply, here is the output:

```
computer
    description: Notebook
    product: Aspire V5-122 (Aspire V5-122_080D_2.10)
    vendor: Acer
    version: V2.10
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: chassis=notebook family=Kabini sku=Aspire V5-122_080D_2.10 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Aspire V5-122
       vendor: Acer
       physical id: 0
       version: V2.10
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V2.10
          date: 10/14/2013
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb uefi
     *-cpu
          description: CPU
          product: AMD A4-1250 APU with Radeon(TM) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD A4-1250 APU with Radeon(TM) HD Graphics
          serial: [REMOVED]
          slot: Socket FT1
          size: 800MHz
          capacity: 1GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb perfctr_l2 arat xsaveopt hw_pstate proc_feedback npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 800 MHz (1,2 ns)
             product: AM1L16BC2P1-B1FS
             vendor: A-DATA Technology
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 667 MHz (1,5 ns)
             vendor: ELPIDA
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: Family 16h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Kabini [Radeon HD 8210]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:75 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:2000(size=256) memory:f0900000-f093ffff memory:f0960000-f097ffff
        *-multimedia:0
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:76 memory:f0940000-f0943fff
        *-pci
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:50 memory:f0800000-f08fffff
           *-network
                description: Wireless interface
                product: BCM43142 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:32 memory:f0800000-f0807fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0948000-f0949fff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:2118(size=8) ioport:2124(size=4) ioport:2110(size=8) ioport:2120(size=4) ioport:2100(size=16) memory:f094f000-f094f3ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f094e000-f094efff
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f094d000-f094d0ff
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f094c000-f094cfff
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f094b000-f094b0ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:77 memory:f0944000-f0947fff
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
        *-generic
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 01
             width: 64 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=sdhci-pci latency=39
             resources: irq:16 memory:f094a000-f094a0ff
     *-pci:1
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 16h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 16h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 16h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 16h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 16h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000LPVX-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=4c189dd1-bde7-4097-a4da-5ee53f991fc7 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 398MiB
                capacity: 399MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-01-15 01:24:19 filesystem=ntfs label=Recovery modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 279MiB
                capacity: 299MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: [REMOVED]
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: [REMOVED]
                size: 227GiB
                capacity: 227GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-11-23 11:32:01 filesystem=ntfs label=Acer name=Basic data partition state=clean
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: [REMOVED]
                size: 16GiB
                capacity: 16GiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-01-15 01:24:28 filesystem=ntfs label=Push Button Reset modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:5
                description: EXT4 volume
                vendor: Linux
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 46GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-10 02:11:29 filesystem=ext4 lastmountpoint=/ modified=2014-12-18 18:43:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-18 18:43:14 state=mounted
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /home
                version: 1.0
                serial: [REMOVED]
                size: 167GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-10 02:11:35 filesystem=ext4 lastmountpoint=/home modified=2014-12-18 18:43:16 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-12-18 18:43:16 state=mounted
           *-volume:7
                description: Linux swap volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                version: 1
                serial: [REMOVED]
                size: 7627MiB
                capacity: 7628MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
```

---

### Post by mörgæs on 2014-12-18
Hardware looks fine. 
Have you tried running **top** while doing normal tasks to see if anything causes a heavy CPU load?

---

