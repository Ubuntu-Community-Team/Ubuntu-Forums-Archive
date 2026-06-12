---
title: "Ubuntu 14.04 extremely high load"
date: 2014-11-21
forum: General Help
---

### Post by blnl on 2014-11-21
I was using Ubuntu 13.04 for about two years without any performance issues om my good old HP Compaq DC7100. Ever since I upgraded to 14.04 my machine is almost continuously suffering from extremely high loads. The load is rarely falling blow 2, while it often goes up to 5-6 (the machine becomes so unresponsive, practically unusable).
At first I thought that something went wrong during the upgrade, so I formated the partition and installed a fresh copy of Ubuntu 14.04 LTS, but it did not help at all. Then I formated the partition once more and installed a fresh copy Ubuntu 13.04 LTS, and now my computer is working normally again.

What is it about 14.04 release that chokes my computer?

I'm using 14.04 in a same way as 13.04, nothing extra heavy is installed or running on my machine. I also do not see any significant difference between the user interfaces of these two versions. So what's going on here?

---

### Post by QIII on 2014-11-21
Hello!

"2" and "5-6" what?  GB of RAM?

We don't know what might have been using up your resources.

The only way for us to help would be for you to reinstsll 14.04 and run ```
 top 
``` in the terminal and post the results.

Cheers!

---

### Post by ajgreeny on 2014-11-21
If your machine is the same or similar spec to this which is what I found for that model desktop
```
Processor
    Processor make Intel
    CPU family Pentium 4
    Processor speed 2.8 GHz
    Number of CPUs 1
    Number of cores (per CPU) Single-core
    Hyperthreading Yes
Video
    Graphics adapter Integrated
    Graphics (integrated) Intel
    Video outputs VGA
```I suspect that you would do much better with Xubuntu, or even better Lubuntu.
How much ram do you have?

---

### Post by mörgæs on 2014-11-22
Yes, some more hardware info would be nice. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by blnl on 2014-11-22
I upgraded to 14.04 again...

This is the top output:
```
top - 17:34:49 up 7 days, 19:14,  4 users,  load average: 3,09, 2,41, 1,13
Tasks: 260 total,   1 running, 259 sleeping,   0 stopped,   0 zombie
%Cpu(s): 11,7 us,  1,8 sy,  0,0 ni, 86,5 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:   1017756 total,   934824 used,    82932 free,     4604 buffers
KiB Swap:  2368508 total,   904460 used,  1464048 free.   279348 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                       
29532 boris     20   0 1039896 194488  12912 S   9,0 19,1 319:26.31 firefox                                                                                       
12350 boris     20   0  297828  11548   5664 S   6,0  1,1  91:34.09 gnome-system-mo                                                                               
 1521 root      20   0  222740  35692  15520 S   4,6  3,5 112:58.39 Xorg                                                                                          
 2319 boris     20   0  627056  35360  10412 S   2,7  3,5  91:13.31 compiz                                                                                        
 6328 boris     20   0  380496  21172   3236 S   2,3  2,1  37:15.04 plugin-containe                                                                               
 2385 boris     20   0   69820   6124   2880 S   1,0  0,6  28:25.00 indicator-multi                                                                               
 9290 boris     20   0    5568   1520   1036 R   0,7  0,1   0:00.06 top                                                                                           
  706 message+  20   0    5208   1868    764 S   0,3  0,2   0:31.02 dbus-daemon                                                                                   
 2226 boris     20   0  201156  15792   6176 S   0,3  1,6  15:53.85 unity-panel-ser                                                                               
 2375 boris     20   0   38512   1804   1456 S   0,3  0,2   6:43.98 indicator-appli                                                                               
 4575 boris     20   0  212400   9848   5440 S   0,3  1,0  20:25.13 gnome-terminal                                                                                
15926 boris     20   0  791356 124920  11616 S   0,3 12,3  74:34.69 nuvolaplayer                                                                                  
    1 root      20   0    4568   1772    840 S   0,0  0,2   0:05.51 init                                                                                          
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.03 kthreadd                                                                                      
    3 root      20   0       0      0      0 S   0,0  0,0   9:54.81 ksoftirqd/0                                                                                   
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                                                                  
    7 root      20   0       0      0      0 S   0,0  0,0   2:24.41 rcu_sched                                                                                     
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                                                        
    9 root      rt   0       0      0      0 S   0,0  0,0   0:01.36 migration/0                                                                                   
   10 root      rt   0       0      0      0 S   0,0  0,0   0:01.19 watchdog/0                                                                                    
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.56 watchdog/1                                                                                    
   12 root      rt   0       0      0      0 S   0,0  0,0   0:00.93 migration/1                                                                                   
   13 root      20   0       0      0      0 S   0,0  0,0   9:55.26 ksoftirqd/1                                                                                   
   15 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:0H                                                                                  
   16 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 khelper                                                                                       
   17 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs                                                                                     
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns                                                                                         
   19 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback                                                                                     
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd                                                                                   
   21 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                        
   23 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd                                                                                       
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff                                                                                       
   25 root      20   0       0      0      0 S   0,0  0,0   0:00.01 khubd                                                                                         

```

Here is more hardware info:

```
computer
    description: Mini Tower Computer
    product: HP Compaq dc7100 CMT(DX438AV) ()
    vendor: Hewlett-Packard
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0968h
       vendor: Hewlett-Packard
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786C1 v01.05
          date: 06/16/2004
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.1
          serial: [REMOVED]
          slot: XU1 PROCESSOR
          size: 3200MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 1MiB
             capacity: 4MiB
             capabilities: burst internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory:0
          description: System Memory
          physical id: 33
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: M3 68L3223ETM-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 0
             serial: [REMOVED]
             slot: XMM1
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 1
             serial: [REMOVED]
             slot: XMM2
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: M3 68L3223ETM-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 2
             serial: [REMOVED]
             slot: XMM3
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 3
             serial: [REMOVED]
             slot: XMM4
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 34
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe00000-cfe7ffff ioport:3800(size=8) memory:e0000000-efffffff memory:cff00000-cff3ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82915G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:cfe80000-cfefffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:7000(size=4096) memory:f0200000-f04fffff ioport:40400000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
                resources: irq:17 memory:f0400000-f040ffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:3440(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3460(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:3480(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:34a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:cff40000-cff403ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:1000(size=4096) memory:f0500000-f07fffff ioport:40600000(size=1048576)
           *-network
                description: Wireless interface
                product: RT2561/RT61 rev B 802.11g
                vendor: Ralink corp.
                physical id: 4
                bus info: pci@0000:05:04.0
                logical name: wlan0
                version: 00
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci driverversion=3.13.0-39-generic firmware=0.8 ip=[REMOVED] latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:f0500000-f0507fff
           *-storage
                description: RAID bus controller
                product: PCI0680 Ultra ATA-133 Host Controller
                vendor: Silicon Image, Inc.
                physical id: 9
                bus info: pci@0000:05:09.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list rom
                configuration: driver=pata_sil680 latency=32
                resources: irq:18 ioport:1010(size=8) ioport:1020(size=4) ioport:1018(size=8) ioport:1024(size=4) ioport:1000(size=16) memory:f0508000-f05080ff memory:40600000-4067ffff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:21 ioport:3000(size=256) ioport:3400(size=64) memory:cff40400-cff405ff memory:cff40600-cff406ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:34e0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:3818(size=8) ioport:3830(size=4) ioport:3820(size=8) ioport:3834(size=4) ioport:34f0(size=16)
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-cdrom:0
             description: DVD-RAM writer
             product: CDDVDW SH-S202N
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             logical name: /media/boris/Fedora 20 x86_64
             version: SB01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             product: CD-Writer+ 9300
             vendor: HP
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sr1
             version: 1.0c
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 4
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HDS728080PLA380
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: PF2O
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00000021
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 25GiB
                capacity: 25GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-11-22 20:29:42 filesystem=ntfs label=System modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: [REMOVED]
                size: 2313MiB
                capacity: 2313MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap label=linux-swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 23GiB
                capacity: 23GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-10-24 00:09:16 filesystem=ext4 label=linux_ubuntu lastmountpoint=/ modified=2014-11-14 22:20:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-11-14 22:20:31 state=mounted
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sda4
                version: 1.0
                serial: [REMOVED]
                size: 23GiB
                capacity: 23GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2011-11-11 23:00:42 filesystem=ext4 label=linux_fedora lastmountpoint=/media/boris/linux_fedora modified=2014-10-23 22:47:26 mounted=2014-10-12 15:28:32 state=clean
     *-scsi:2
          physical id: 6
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HITACHI HDS72505
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: K2AO
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=a27f48fa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: [REMOVED]
                size: 117GiB
                capacity: 117GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-03-06 20:37:59 filesystem=ext4 label=linux_home lastmountpoint=/home modified=2014-10-23 22:47:27 mounted=2014-10-11 19:11:33 state=clean
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdb2
                logical name: /mnt/DC7100data
                version: 1.0
                serial: [REMOVED]
                size: 348GiB
                capacity: 348GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-08-07 23:14:29 filesystem=ext4 label=linux_data lastmountpoint=/mnt/DC7100data modified=2014-11-14 22:20:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-11-14 22:20:32 state=mounted
     *-scsi:3
          physical id: 7
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: SCSI Disk
             product: ZIP 100
             vendor: IOMEGA
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             version: 23.D
             size: 96MiB (100MB)
             capabilities: removable
             configuration: ansiversion=5 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 96MiB (100MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=1f11014e
              *-volume
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 4
                   logical name: /dev/sdc4
                   version: FAT32
                   serial: [REMOVED]
                   size: 95MiB
                   capacity: 95MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
     *-scsi:4
          physical id: 8
          logical name: scsi5
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: WDC WD5000AAKB-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdd
             version: 12.0
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=b1f7b4f7
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdd1
                logical name: /mnt/DC7100back
                version: 1.0
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-09-30 21:11:23 filesystem=ext4 label=linux_backup lastmountpoint=/mnt/DC7100back modified=2014-11-14 22:20:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-11-14 22:20:32 state=mounted
        *-disk:1
             description: SCSI Disk
             physical id: 0.1.0
             bus info: scsi@5:0.1.0
             logical name: /dev/sde
             size: 149GiB (160GB)
             configuration: sectorsize=512

```

---

### Post by mörgæs on 2014-11-22
The processor is fine, but your graphics processor is weak and there's only 1 GiB of memory. I would delete Ubuntu and install X/Lubuntu 14.04.1 or 14.10 as suggested above. 

Also, your hard disks are partitioned in a somewhat complicated manner. I suggest using the opportunity and delete as many partitions as possible before installing. 

Remember to choose 'something else' during install if you want to keep the dual boot with Windows.

---

### Post by blnl on 2014-11-23
> **mörgæs said:**
> The processor is fine, but your graphics processor is weak and there's only 1 GiB of memory. I would delete Ubuntu and install X/Lubuntu 14.04.1 or 14.10 as suggested above. 

Also, your hard disks are partitioned in a somewhat complicated manner. I suggest using the opportunity and delete as many partitions as possible before installing. 

Remember to choose 'something else' during install if you want to keep the dual boot with Windows.

The reason that my HDD's are partitioned as such is because I have Windows, Fedora and Ubuntu on this machine and several large partitions that I use to secure my NAS data while performing NAS maintenance. Therefore, the partitioning scheme is not going to change.

Thanks for suggesting the alternatives.  Still my original question is not answered. Why such a significant performance difference between Ubuntu 13.04 and Ubuntu 14.04?
(The reason that I need Ubuntu is complex and I'm not sure if any alternatives are suitable. I have installed Ubuntu at my mothers computer, so I need to have one Ubuntu partition on my own machine in order to be able to support her when needed (it 's a matter of getting used to the Unity desktop environment). One of the main reasons to chose Ubuntu is the LTS life cycle, which does not require frequent maintenance, hence it does not generate a lot of work for me. So, any alternative, must have an LTS life cycle of at least 3-5 years. Also the desktop environment must be simple to use, i.e. suitable for 65 year old user with poor computer skills)

---

### Post by mörgæs on 2014-11-23
If you want Ubuntu on the computer then adding more memory and / or a better graphics card is an option.

Both Xubuntu and Lubuntu have three years LTS.

---

### Post by scoon on 2014-11-23
Hey there, 

One thing you could look into is changing the kernel scheduler.  A very quick and easy read can be found [HERE]("http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/").  Originally, my kernel was using the deadline scheduler.  I felt that there was more lag than there should be, even for a fresh install.  I switched to the cfq scheduler and my lappy "feels" faster.  I get that I'm talking about feelings and what I perceive, but changing the scheduler really made a difference for me.   This was an easier and cheaper thing to try than to start throwing parts at my lappy or buying a new one.  

Thanks, 

Skip

---

### Post by HousieMousie2 on 2014-11-23
I wish I could help you, blnl, other than to say that I feel your pain.  I too noticed the drastic difference between the two LTS releases (on 3 different machines).  Fortunately for me, I do not need to run Ubuntu and have turned to XFCE to solve my suddenly pokey machine syndrome.

I also wish I knew what had changed so much between them, but I doubt either of us will get that answer.

Best of luck to you!

---

### Post by sandyd on 2014-11-23
> **blnl said:**
> The reason that my HDD's are partitioned as such is because I have Windows, Fedora and Ubuntu on this machine and several large partitions that I use to secure my NAS data while performing NAS maintenance. Therefore, the partitioning scheme is not going to change.

Thanks for suggesting the alternatives.  Still my original question is not answered. Why such a significant performance difference between Ubuntu 13.04 and Ubuntu 14.04?
(The reason that I need Ubuntu is complex and I'm not sure if any alternatives are suitable. I have installed Ubuntu at my mothers computer, so I need to have one Ubuntu partition on my own machine in order to be able to support her when needed (it 's a matter of getting used to the Unity desktop environment). One of the main reasons to chose Ubuntu is the LTS life cycle, which does not require frequent maintenance, hence it does not generate a lot of work for me. So, any alternative, must have an LTS life cycle of at least 3-5 years. Also the desktop environment must be simple to use, i.e. suitable for 65 year old user with poor computer skills)
The load doesn't seem to be CPU bound - that is unless your CPU usage is bouncing around, and you happened to take the output when the cpu was low

However, from the output in your top (below) you have around 1G of data being stored into the swap and around 286+84MB physical RAM free
```
KiB Mem:   1017756 total,   934824 used,    82932 free,     4604 buffers
KiB Swap:  2368508 total,   904460 used,  1464048 free.   279348 cached Mem
```

Converting into MB, which puts things a bit better into perspective... (note, rounded)

```
MB Mem:   1042 total,   957 used,    84 free,     4 buffers
MB Swap:  2425 total,   926 used,  1499 free.   286 cached Mem
```

Check if the swap is thrashing your disk - with 1G of data being in the swap, that could be the case.

You can do this by running the following
```

sudo apt-get install sysstat
iostat

``` or by using iotop

---

### Post by blnl on 2014-11-25
The iostat output looks like this:

```
Linux 3.13.0-39-generic (DC7100-HP) 	25-11-14 	_i686_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          36,30    0,24    6,57    8,37    0,00   48,51

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
scd0              0,00         0,00         0,00        136          0
sda               5,87        51,47        52,53   49206297   50221008
sdb               0,53        32,22         5,98   30806601    5717193
sdc               0,00         0,00         0,00       3576          0
sdd               0,03         0,23         0,00     218303       4656
sde               0,00         0,00         0,00       2133         44

```
```
Linux 3.13.0-39-generic (DC7100-HP) 	25-11-14 	_i686_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          36,34    0,23    6,58    8,30    0,00   48,55

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
scd0              0,00     0,00    0,00    0,00     0,00     0,00     4,77     0,00   91,16   91,16    0,00  91,16   0,00
sda               2,05     4,60    2,36    3,46    50,66    52,33    35,41     0,21   36,76   19,21   48,71   5,67   3,30
sdb               0,07     0,16    0,49    0,03    32,20     5,98   146,18     0,01   12,99    2,16  207,10   2,38   0,12
sdc               0,00     0,00    0,00    0,00     0,00     0,00    17,66     0,00   42,84   42,84    0,00  40,34   0,00
sdd               0,03     0,00    0,02    0,00     0,21     0,00    17,51     0,00    1,46    1,37    8,54   0,88   0,00
sde               0,00     0,00    0,00    0,00     0,00     0,00     8,05     0,00    1,93    1,98    0,24   1,79   0,00

```

My swap partition is located on /dev/sda:
```
/dev/sda1: LABEL="System" UUID="483C9DC73C9DB104" TYPE="ntfs" 
/dev/sda2: LABEL="linux-swap" UUID="bb7bcb99-7f45-4ab8-a644-d16c65388be2" TYPE="swap" 
/dev/sda3: LABEL="linux_ubuntu" UUID="dc203cb7-f60b-40fc-a34e-11f5d4d4ba3a" TYPE="ext4"  are partitioned as follows
/dev/sda4: LABEL="linux_fedora" UUID="46e8d973-9579-4a29-9541-f0a84cb295d8" TYPE="ext4" 
/dev/sdb1: LABEL="linux_home" UUID="f8c4dd33-202d-4ada-8a4f-b4799f4eabfd" TYPE="ext4" 
/dev/sdb2: LABEL="linux_data" UUID="48cd7457-4b0d-4ff5-b920-51afc89cfd13" TYPE="ext4" 
/dev/sdc4: LABEL="ZIP-100" UUID="103D-E8D1" TYPE="vfat" 
/dev/sdd1: LABEL="linux_backup" UUID="4992def9-f106-4a70-91f7-dd6948a8b5f1" TYPE="ext4" 
/dev/sde1: LABEL="linux_temp" UUID="267f0223-39f3-43c7-b621-9561ceec137a" TYPE="ext4" 
```

> **scoon said:**
> Hey there, 

One thing you could look into is changing the kernel scheduler.  A very quick and easy read can be found [HERE]("http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/").  Originally, my kernel was using the deadline scheduler.  I felt that there was more lag than there should be, even for a fresh install.  I switched to the cfq scheduler and my lappy "feels" faster.  I get that I'm talking about feelings and what I perceive, but changing the scheduler really made a difference for me.   This was an easier and cheaper thing to try than to start throwing parts at my lappy or buying a new one.  

Thanks, 

Skip

My scheduler is also deadline
```
boris@DC7100-HP:~$ cat /sys/block/sdb/queue/scheduler
noop [deadline] cfq 

```

I'll switch to cfq and see what happens.
(I wish that I new what was the scheduler setting for 13.04 release)

There seems to be a problem with setting the scheduler
```
root@DC7100-HP:/home/boris# echo cfg >  /sys/block/sda/queue/scheduler
bash: echo: write error: Invalid argument
```

> **HousieMousie2 said:**
> I wish I could help you, blnl, other than to say that I feel your pain.  I too noticed the drastic difference between the two LTS releases (on 3 different machines).  Fortunately for me, I do not need to run Ubuntu and have turned to XFCE to solve my suddenly pokey machine syndrome.

I also wish I knew what had changed so much between them, but I doubt either of us will get that answer.

Best of luck to you!

Thanks a lot for posting your experience. Good to know that I'm not alone here.
By the way, my mothers laptop is also suffering from significantly reduced performance. However, that hardware is much newer so it is still OK, while my machine really chokes to the point that every mouse click takes 30 seconds to execute.

Comments like your hardware is too old, I do not buy it. Something is really screwed up in 14.04.
Of course if you trow enough hardware at it, anything will work, but that sounds more like Windows strategy. I sincerely hope that Canonical is not following Microsoft footsteps...

---

### Post by scoon on 2014-11-26
> **blnl said:**
> My scheduler is also deadline
```
boris@DC7100-HP:~$ cat /sys/block/sdb/queue/scheduler
noop [deadline] cfq 

```

I'll switch to cfq and see what happens.
(I wish that I new what was the scheduler setting for 13.04 release)

There seems to be a problem with setting the scheduler
```
root@DC7100-HP:/home/boris# echo cfg >  /sys/block/sda/queue/scheduler
bash: echo: write error: Invalid argument
```

Hey there, 

You need to echo cf**q**.  It looks like you tried cf**g**.

Thanks, 

Skip

---

### Post by blnl on 2014-11-26
> **scoon said:**
> Hey there, 

You need to echo cf**q**.  It looks like you tried cf**g**.

Thanks, 

Skip

Of course, it was late, I was not awake :oops:

I have changed scheduler to "cfq" for all my drives.
```
root@DC7100-HP:/home/boris# echo cfq >  /sys/block/sda/queue/scheduler
root@DC7100-HP:/home/boris# echo cfq >  /sys/block/sdb/queue/scheduler
root@DC7100-HP:/home/boris# echo cfq >  /sys/block/sdc/queue/scheduler
root@DC7100-HP:/home/boris# echo cfq >  /sys/block/sdd/queue/scheduler
root@DC7100-HP:/home/boris# echo cfq >  /sys/block/sde/queue/scheduler
root@DC7100-HP:/home/boris# cat /sys/block/sd*/queue/scheduler
noop deadline [cfq] 
noop deadline [cfq] 
noop deadline [cfq] 
noop deadline [cfq] 
noop deadline [cfq] 

```

However, after rebooting my computer scheduler is reset back to "deadline".
```
root@DC7100-HP:/home/boris# cat /sys/block/sd*/queue/scheduler
noop [deadline] cfq 
noop [deadline] cfq 
noop [deadline] cfq 
noop [deadline] cfq 
noop [deadline] cfq 

```

---

### Post by scoon on 2014-11-26
> **blnl said:**
> 
However, after rebooting my computer scheduler is reset back to "deadline".
```
root@DC7100-HP:/home/boris# cat /sys/block/sd*/queue/scheduler
noop [deadline] cfq 
noop [deadline] cfq 
noop [deadline] cfq 
noop [deadline] cfq 
noop [deadline] cfq 
```

Hey there, 

The second poster gave this [LINK]("http://www.redhat.com/magazine/008jun05/features/schedulers/") explaining how to make the change permanent.

Thanks, 

Skip

---

### Post by blnl on 2014-11-26
> **scoon said:**
> Hey there, 

The second poster gave this [LINK]("http://www.redhat.com/magazine/008jun05/features/schedulers/") explaining how to make the change permanent.

Thanks, 

Skip

I was not able to implement permanent elevator option in /boot/grub/grub.conf (since grub2 is introduced the syntax is incomprehensible and I do not want mess with it)
Instead, I have entered "echo cfq" lines in /etc/rc.local

My first impression is that it really helps, load is definitely tempered (it stays in the range 1-2). I did not yet see extreme values, except during startup it goes briefly up to 4.5.
I'll wait a few days, to observe the behavior before marking this thread solved.

(Have to admit that I'm tempted to install 13.04 just to check the default scheduler setup :roll:)

---

### Post by scoon on 2014-11-27
> **blnl said:**
> I was not able to implement permanent elevator option in /boot/grub/grub.conf (since grub2 is introduced the syntax is incomprehensible and I do not want mess with it)
Instead, I have entered "echo cfq" lines in /etc/rc.local

My first impression is that it really helps, load is definitely tempered (it stays in the range 1-2). I did not yet see extreme values, except during startup it goes briefly up to 4.5.
I'll wait a few days, to observe the behavior before marking this thread solved.

(Have to admit that I'm tempted to install 13.04 just to check the default scheduler setup :roll:)

Hey there, 

Glad to hear.  I've been doing some searching around the internet looking for other schedulers to try.  I vaguely remember seeing something that the default scheduler was cfq but for some reason got changed to deadline. 

Thanks, 

Skip

---

### Post by blnl on 2014-11-27
Just had a quick look at my Fedora 20 scheduler settings:
```
[boris@E7440-DELL ~]$ cat /sys/block/sd*/queue/scheduler
noop deadline [cfq] 

```

I'm convinced now that cfq is the superior scheduler. I'll make a new entry in my Ubuntu installation checklist to check the scheduler setting.

This is already second serious issue that Ubuntu 14.04 is suffering from. The first serious problem is that the network manager does not wake up when computer is resuming from standby, I had to patch that manually as well.
Compared to 13.04, quality of 14.04 release is somewhat disappointing, let's hope that Ubuntu 15.04 will do better...

---

### Post by mörgæs on 2014-11-28
If you have the time it would be interesting if you could test the 15.04 daily build.

---

### Post by blnl on 2014-11-29
> **mörgæs said:**
> If you have the time it would be interesting if you could test the 15.04 daily build.

Unfortunately, time is not the luxury that I have. However, if I decide to make Ubuntu main OS on this machine, Fedora partition will become obsolete. Then I might try 15.04 daily build...  

PS. I'll follow your previous advice and upgrade the memory to 4GB. (The PC is old, but I see there is still life in it. With a bit of tweaking it can decently run Ubuntu.)

---

