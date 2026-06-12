---
title: "System slower then on much worst machine how to investigate"
date: 2013-01-10
forum: General Help
---

### Post by Berduchwal on 2013-01-10
I have switched to a differen machine today and Ubuntu 12.10 works slower on this more powerfull pc.

For example it takes 6seconds to open home folder or when I type this courser move slower then I type...

Some initial diagnostics:

sudo lshw

```

skrybapc1-desktop         
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: G41M-S3
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.40
          date: 01/12/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU 2.53GHz
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 2533MHz
          capacity: 2533MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc up pebs bts nopl pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
          configuration: cores=1 enabledcores=1 threads=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 4GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fd000000-febfffff ioport:de000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:de000000-dfffffff ioport:ec00(size=128) memory:fe000000-fe07ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:febfc000-febfffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:fcefc000-fcefffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:dc000000-dc3fffff ioport:ddf00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:fcf00000-fcffffff ioport:dde00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:25:22:a9:90:78
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:d800(size=256) memory:ddeff000-ddefffff memory:ddee0000-ddeeffff memory:fcfe0000-fcffffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c480(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c800(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c880(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:cc00(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fcefbc00-fcefbfff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250312AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: JC45
             serial: 5VMQ3VF0
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000980b1
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: fdc5d569-b66d-4593-b399-278d313853e3
                size: 228GiB
                capacity: 228GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-10-20 10:39:25 filesystem=ext4 lastmountpoint=/ modified=2013-01-10 14:24:07 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-01-10 14:24:08 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 4094MiB
                capacity: 4094MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4094MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7260S
             vendor: Optiarc
             physical id: 0.1.0
             bus info: scsi@3:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:3
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
     *-scsi:3
          physical id: 5
          bus info: usb@1:7
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             configuration: sectorsize=512
```

cat /proc/cpuinfo

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Celeron(R) CPU 2.53GHz
stepping	: 1
microcode	: 0x17
cpu MHz		: 2527.025
cache size	: 256 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc up pebs bts nopl pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
bogomips	: 5054.05
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

cat /proc/meminfo


```
MemTotal:        4046880 kB
MemFree:         2240744 kB
Buffers:           86272 kB
Cached:           811504 kB
SwapCached:            0 kB
Active:          1078792 kB
Inactive:         522104 kB
Active(anon):     709940 kB
Inactive(anon):      732 kB
Active(file):     368852 kB
Inactive(file):   521372 kB
Unevictable:       31272 kB
Mlocked:           31272 kB
SwapTotal:       4192252 kB
SwapFree:        4192252 kB
Dirty:               128 kB
Writeback:             0 kB
AnonPages:        734412 kB
Mapped:           152732 kB
Shmem:              1728 kB
Slab:              81620 kB
SReclaimable:      56104 kB
SUnreclaim:        25516 kB
KernelStack:        3480 kB
PageTables:        30236 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6215692 kB
Committed_AS:    3472572 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      129964 kB
VmallocChunk:   34359608187 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       44544 kB
DirectMap2M:     4149248 kB

```

top

```
top - 16:31:10 up  2:07,  2 users,  load average: 1.20, 1.87, 1.78
Tasks: 165 total,   5 running, 160 sleeping,   0 stopped,   0 zombie
%Cpu(s): 26.3 us, 11.3 sy,  0.0 ni, 60.8 id,  1.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4046880 total,  1810268 used,  2236612 free,    86376 buffers
KiB Swap:  4192252 total,        0 used,  4192252 free,   811592 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1853 marcin    20   0 1068m  91m  34m R  11.9  2.3  10:43.61 compiz            
 1120 root      20   0  174m  50m 8196 S   8.0  1.3  12:04.08 Xorg              
 2046 marcin    20   0  557m  46m  11m R   5.0  1.2   7:31.40 unity-panel-ser   
 2048 marcin    20   0  369m 8800 3536 R   3.3  0.2   5:06.89 hud-service       
 3665 marcin    20   0  531m  18m  11m S   3.0  0.5   0:05.36 gnome-terminal    
 1869 marcin    20   0  498m  12m 8596 S   2.0  0.3   2:36.23 indicator-multi   
 2162 marcin    20   0  425m 5636 3940 R   1.7  0.1   1:48.67 indicator-appli   
 3092 marcin    20   0  405m  36m  23m S   1.3  0.9   1:13.69 plugin-containe   
 1813 marcin    20   0 27032 3408  728 S   0.7  0.1   1:06.88 dbus-daemon       
 2036 marcin    20   0  309m  11m 8724 S   0.7  0.3   0:05.58 gtk-window-deco   
 2508 marcin    20   0 1125m 228m  43m S   0.7  5.8  12:36.56 firefox           
 3748 marcin    20   0 27240 1592 1128 R   0.7  0.0   0:00.05 top               
 1831 marcin    20   0  709m  19m  12m S   0.3  0.5   0:06.13 gnome-settings-   
 1870 marcin    20   0  956m  43m  20m S   0.3  1.1   2:12.44 nautilus          
 1891 marcin    20   0 1091m  83m  19m S   0.3  2.1   1:14.31 dropbox           
 2009 marcin    20   0  396m  11m 7972 S   0.3  0.3   0:28.17 bamfdaemon        
    1 root      20   0 24444 2368 1284 S   0.0  0.1   0:01.14 init              
top - 16:31:52 up  2:07,  2 users,  load average: 0.78, 1.67, 1.72
Tasks: 165 total,   2 running, 163 sleeping,   0 stopped,   0 zombie
%Cpu(s): 31.9 us, 12.1 sy,  0.0 ni, 56.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4046880 total,  1811136 used,  2235744 free,    86456 buffers
KiB Swap:  4192252 total,        0 used,  4192252 free,   811596 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                 
 1120 root      20   0  174m  50m 8196 R  11.2  1.3  12:07.03 Xorg                                    
 1853 marcin    20   0 1068m  91m  34m S   9.2  2.3  10:46.98 compiz                                  
 3665 marcin    20   0  531m  18m  11m S   5.9  0.5   0:06.55 gnome-terminal                          
 2046 marcin    20   0  557m  46m  11m S   5.3  1.2   7:33.57 unity-panel-ser                         
 2048 marcin    20   0  369m 8800 3536 S   3.6  0.2   5:08.50 hud-service                             
 3092 marcin    20   0  405m  36m  23m S   2.3  0.9   1:14.28 plugin-containe                         
 2162 marcin    20   0  425m 5636 3940 S   2.0  0.1   1:49.35 indicator-appli                         
 1869 marcin    20   0  498m  12m 8596 S   1.7  0.3   2:37.07 indicator-multi                         
 1813 marcin    20   0 27032 3408  728 S   1.0  0.1   1:07.22 dbus-daemon                             
 1822 marcin    20   0  121m 3276 2708 S   0.3  0.1   0:01.93 at-spi2-registr                         
 1831 marcin    20   0  709m  19m  12m S   0.3  0.5   0:06.21 gnome-settings-                         
 1934 marcin    20   0  283m 3260 2632 S   0.3  0.1   0:01.65 gvfs-afc-volume                         
 2009 marcin    20   0  396m  11m 7972 S   0.3  0.3   0:28.29 bamfdaemon                              
 2508 marcin    20   0 1125m 228m  43m S   0.3  5.8  12:36.88 firefox                                 
    1 root      20   0 24444 2368 1284 S   0.0  0.1   0:01.14 init                                    
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd                                
    3 root      20   0     0    0    0 S   0.0  0.0   0:02.59 ksoftirqd/0                             
    5 root      20   0     0    0    0 S   0.0  0.0   0:00.48 kworker/u:0                             
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/0                             
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.28 watchdog/0                              
    8 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cpuset                                  
    9 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper                                 
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs                               
   11 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 netns                                   
   12 root      20   0     0    0    0 S   0.0  0.0   0:00.19 sync_supers                             


```

I would appreciate some help in learning why is my pc running so slow.

---

### Post by Paqman on 2013-01-10
You seem to be runnning on the open source Nouveau driver. Try installing the proprietary Nvidia drivers.

---

### Post by Berduchwal on 2013-01-10
Ok I did that:

System Settings>Software Sources>Additional Drivers

There I changed for Nvidia binary (tested, proprietary) 

After a reset I do not see a change. Any other suggestions?

---

