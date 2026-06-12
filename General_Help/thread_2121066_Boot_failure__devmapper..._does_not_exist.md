---
title: "Boot failure  /dev/mapper... does not exist"
date: 2013-02-28
forum: General Help
---

### Post by NibbleAbit on 2013-02-28
I upgraded to 12.04 and now my system won't boot.  It complains about /dev/mapper/isw...Volume01 does not exist and drops me to busybox.

I have surfed around and found some commands that I don't really understand, but here is what I think is useful.


    ls /dev/mapper/
        control
        isw...Volume0 -> ../dm-0
        isw...Volume0p1 -> ../dm-1
        isw...Volume0p2 -> ../dm-2
        isw...Volume0p5 -> ../dm-3

`cat /proc/cmdline` tells me it is indeed trying `Volume01`.

`dmraid -ay` tells me that that the volumes that exist are already active.

I'm now running off a Ubuntu Live CD.  It can see my hard disk, but I can't edit anything of value, since I can't sudo.  (and I wouldn't know what to edit anyway)

Which volume is the right volume to tell grub to boot from and what do I type in busybox to tell it to do so?

Any assistance would be most appreciated.

I have more info.  I'll try to be as precise as I can so the next guy doesn't get as lost as I did.  I have no idea how to interpret anything.

From the Live CD, I could see my drive.  First, I had to open my file browser and click on my drive so that it mounted.  Then I found a script called bootinfoscript (Sorry, I lost the link, LiveCD does not hold bookmarks well).  I downloaded it, and opened another folder (right-click on the folder icon) to my Downloads, double click it to unpack and save in my hard drive's /tmp folder.

Reboot and remove the CD to get back to the BusyBox.

    mkdir /mnt
    mount /dev/mapper/randomNameVolume0p1 /mnt -- I tried all the files here until one worked
    mdadm --examine --scan --config=mdadm.con > /mnt/tmp/mdadm.txt
    dmraid -r > /mnt/tmp/dmraid.txt
    ls -l /dev/mapper > mapper.txt
    chroot /mnt
    mount /proc
    cd /tmp
    cat /proc/partitions | strings > partitions.txt
    dmesg | grep sd[ab] > dmesg.txt
    lshw > lshw.txt
    ./bootinfoscript
    ^d
    exit

Reboot to the LiveCD, open my folder to my hard disk, go to the tmp folder, double click on the txt files I created and copy/paste the info

dmraid.txt

    /dev/sdb: isw, "isw_bhibhcjiba", GROUP, ok, 976773166 sectors, data@ 0
    /dev/sda: isw, "isw_bhibhcjiba", GROUP, ok, 976773166 sectors, data@ 0

mapper.txt

    crw-------    1   10, 236 control
    lrwxrwxrwx    1         7 isw_bhibhcjiba_Volume0 -> ../dm-0
    lrwxrwxrwx    1         7 isw_bhibhcjiba_Volume0p5 -> ../dm-3
    lrwxrwxrwx    1         7 isw_bhibhcjiba_Volume0p1 -> ../dm-1
    lrwxrwxrwx    1         7 isw_bhibhcjiba_Volume0p2 -> ../dm-2

partitions.txt

    major minor  #blocks  name
       8        0  488386584 sda
       8       16  488386584 sdb
      11        0    1048575 sr0
     252        0  488383620 dm-0
     252        1  468575856 dm-1
     252        2   19800112 dm-2
     252        3   19800081 dm-3

dmesg.txt

    [    1.331382] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
    [    1.331446] sd 0:0:0:0: [sda] Write Protect is off
    [    1.331449] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
    [    1.331487] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [    1.373526]  sda: sda1 sda2 < sda5 >
    [    1.373868] sd 0:0:0:0: [sda] Attached SCSI disk
    [    2.142733] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
    [    2.142775] sd 2:0:0:0: [sdb] Write Protect is off
    [    2.142778] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
    [    2.142796] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    [    2.191869]  sdb: sdb1 sdb2 < sdb5 >
    [    2.192188] sd 2:0:0:0: [sdb] Attached SCSI disk

lshw.txt

    _none_
        description: Desktop Computer
        product: System Product Name (To Be Filled By O.E.M.)
        vendor: System manufacturer
        version: System Version
        serial: System Serial Number
        width: 64 bits
        capabilities: smbios-2.5 dmi-2.5 vsyscall32
        configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=A0DF001E-8C00-00C5-D544-E0CB4E54D129
      *-core
           description: Motherboard
           product: P5Q-EM DO
           vendor: ASUSTeK Computer INC.
           physical id: 0
           version: Rev 1.xx
           serial: 103168810001969
           slot: To Be Filled By O.E.M.
         *-firmware
              description: BIOS
              vendor: American Megatrends Inc.
              physical id: 0
              version: 1102
              date: 05/27/2009
              size: 64KiB
              capacity: 1984KiB
              capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
         *-cpu
              description: CPU
              product: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz
              vendor: Intel Corp.
              physical id: 4
              bus info: cpu@0
              version: Intel(R) Core(TM)2 Quad CPU Q8400 @ 2.66GHz
              serial: To Be Filled By O.E.M.
              slot: LGA 775
              size: 2666MHz
              capacity: 3800MHz
              width: 64 bits
              clock: 333MHz
              capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
              configuration: cores=4 enabledcores=4 threads=4
            *-cache:0
                 description: L1 cache
                 physical id: 5
                 slot: L1-Cache
                 size: 128KiB
                 capacity: 128KiB
                 capabilities: internal write-back data
            *-cache:1
                 description: L2 cache
                 physical id: 6
                 slot: L2-Cache
                 size: 4MiB
                 capacity: 4MiB
                 capabilities: internal write-back unified
         *-memory
              description: System Memory
              physical id: 37
              slot: System board or motherboard
              size: 8GiB
            *-bank:0
                 description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
                 product: ModulePartNumber00
                 vendor: Manufacturer00
                 physical id: 0
                 serial: SerNum00
                 slot: DIMM0
                 size: 4GiB
                 width: 64 bits
                 clock: 800MHz (1.2ns)
            *-bank:1
                 description: DIMM [empty]
                 product: ModulePartNumber01
                 vendor: Manufacturer01
                 physical id: 1
                 serial: SerNum01
                 slot: DIMM1
            *-bank:2
                 description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
                 product: ModulePartNumber02
                 vendor: Manufacturer02
                 physical id: 2
                 serial: SerNum02
                 slot: DIMM2
                 size: 4GiB
                 width: 64 bits
                 clock: 800MHz (1.2ns)
            *-bank:3
                 description: DIMM [empty]
                 product: ModulePartNumber03
                 vendor: Manufacturer03
                 physical id: 3
                 serial: SerNum03
                 slot: DIMM3
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
               *-display UNCLAIMED
                    description: VGA compatible controller
                    product: RV710 [Radeon HD 4350]
                    vendor: Hynix Semiconductor (Hyundai Electronics)
                    physical id: 0
                    bus info: pci@0000:01:00.0
                    version: 00
                    size: 256MiB
                    width: 64 bits
                    clock: 33MHz
                    capabilities: pm pciexpress msi vga_controller bus_master cap_list
                    configuration: latency=0
                    resources: iomemory:d0000000-dfffffff iomemory:fe9e0000-fe9effff ioport:d000(size=256) irq:10
               *-multimedia UNCLAIMED
                    description: Audio device
                    product: RV710/730 HDMI Audio [Radeon HD 4000 series]
                    vendor: Hynix Semiconductor (Hyundai Electronics)
                    physical id: 0.1
                    bus info: pci@0000:01:00.1
                    version: 00
                    width: 64 bits
                    clock: 33MHz
                    capabilities: pm pciexpress msi bus_master cap_list
                    configuration: latency=0
                    resources: iomemory:fe9fc000-fe9fffff irq:11
            *-communication UNCLAIMED
                 description: Communication controller
                 product: 4 Series Chipset HECI Controller
                 vendor: Intel Corporation
                 physical id: 3
                 bus info: pci@0000:00:03.0
                 version: 03
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi bus_master cap_list
                 configuration: latency=0
                 resources: iomemory:fe8ff000-fe8ff00f irq:10
            *-network DISABLED
                 description: Ethernet interface
                 product: 82567LM-3 Gigabit Network Connection
                 vendor: Intel Corporation
                 physical id: 19
                 bus info: pci@0000:00:19.0
                 logical name: eth0
                 version: 02
                 serial: e0:cb:4e:54:d1:29
                 size: 1Gbit/s
                 capacity: 1Gbit/s
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.4-3 latency=0 link=no multicast=yes port=twisted pair speed=1Gbit/s
                 resources: iomemory:fe8c0000-fe8dffff iomemory:fe8fe000-fe8fefff ioport:cc00(size=32) irq:48
            *-usb:0 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB UHCI Controller #4
                 vendor: Intel Corporation
                 physical id: 1a
                 bus info: pci@0000:00:1a.0
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: latency=0
                 resources: ioport:c480(size=32) irq:16
            *-usb:1 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB UHCI Controller #5
                 vendor: Intel Corporation
                 physical id: 1a.1
                 bus info: pci@0000:00:1a.1
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: latency=0
                 resources: ioport:c800(size=32) irq:21
            *-usb:2 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB UHCI Controller #6
                 vendor: Intel Corporation
                 physical id: 1a.2
                 bus info: pci@0000:00:1a.2
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: latency=0
                 resources: ioport:c880(size=32) irq:18
            *-usb:3 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2
                 vendor: Intel Corporation
                 physical id: 1a.7
                 bus info: pci@0000:00:1a.7
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm debug ehci bus_master cap_list
                 configuration: latency=0
                 resources: iomemory:fe8fd000-fe8fd3ff irq:18
            *-multimedia UNCLAIMED
                 description: Audio device
                 product: 82801JD/DO (ICH10 Family) HD Audio Controller
                 vendor: Intel Corporation
                 physical id: 1b
                 bus info: pci@0000:00:1b.0
                 version: 02
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi pciexpress bus_master cap_list
                 configuration: latency=0
                 resources: iomemory:fe8f4000-fe8f7fff irq:3
            *-pci:1
                 description: PCI bridge
                 product: 82801JD/DO (ICH10 Family) PCI Express Port 1
                 vendor: Intel Corporation
                 physical id: 1c
                 bus info: pci@0000:00:1c.0
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
            *-pci:2
                 description: PCI bridge
                 product: 82801JD/DO (ICH10 Family) PCI Express Port 5
                 vendor: Intel Corporation
                 physical id: 1c.4
                 bus info: pci@0000:00:1c.4
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
               *-ide UNCLAIMED
                    description: IDE interface
                    product: 88SE6101/6102 single-port PATA133 interface
                    vendor: Marvell Technology Group Ltd.
                    physical id: 0
                    bus info: pci@0000:02:00.0
                    version: c0
                    width: 32 bits
                    clock: 33MHz
                    capabilities: ide pm msi pciexpress bus_master cap_list
                    configuration: latency=0
                    resources: ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) iomemory:feaff000-feaff1ff irq:16
            *-usb:4 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB UHCI Controller #1
                 vendor: Intel Corporation
                 physical id: 1d
                 bus info: pci@0000:00:1d.0
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: latency=0
                 resources: ioport:c000(size=32) irq:23
            *-usb:5 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB UHCI Controller #2
                 vendor: Intel Corporation
                 physical id: 1d.1
                 bus info: pci@0000:00:1d.1
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: latency=0
                 resources: ioport:c080(size=32) irq:19
            *-usb:6 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB UHCI Controller #3
                 vendor: Intel Corporation
                 physical id: 1d.2
                 bus info: pci@0000:00:1d.2
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: latency=0
                 resources: ioport:c400(size=32) irq:18
            *-usb:7 UNCLAIMED
                 description: USB controller
                 product: 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1
                 vendor: Intel Corporation
                 physical id: 1d.7
                 bus info: pci@0000:00:1d.7
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm debug ehci bus_master cap_list
                 configuration: latency=0
                 resources: iomemory:fe8fc000-fe8fc3ff irq:23
            *-pci:3
                 description: PCI bridge
                 product: 82801 PCI Bridge
                 vendor: Intel Corporation
                 physical id: 1e
                 bus info: pci@0000:00:1e.0
                 version: a2
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pci subtractive_decode bus_master cap_list
               *-firewire UNCLAIMED
                    description: FireWire (IEEE 1394)
                    product: FW322/323
                    vendor: LSI Corporation
                    physical id: 3
                    bus info: pci@0000:04:03.0
                    version: 70
                    width: 32 bits
                    clock: 33MHz
                    capabilities: pm ohci bus_master cap_list
                    configuration: latency=64 maxlatency=24 mingnt=12
                    resources: iomemory:febff000-febfffff irq:19
            *-isa
                 description: ISA bridge
                 product: 82801JDO (ICH10DO) LPC Interface Controller
                 vendor: Intel Corporation
                 physical id: 1f
                 bus info: pci@0000:00:1f.0
                 version: 02
                 width: 32 bits
                 clock: 33MHz
                 capabilities: isa bus_master cap_list
                 configuration: latency=0
            *-storage
                 description: RAID bus controller
                 product: 82801 SATA Controller [RAID mode]
                 vendor: Intel Corporation
                 physical id: 1f.2
                 bus info: pci@0000:00:1f.2
                 logical name: scsi0
                 logical name: scsi2
                 logical name: scsi4
                 version: 02
                 width: 32 bits
                 clock: 66MHz
                 capabilities: storage msi pm bus_master cap_list emulated
                 configuration: latency=0
                 resources: ioport:b880(size=8) ioport:b800(size=4) ioport:b480(size=8) ioport:b400(size=4) ioport:b080(size=32) iomemory:fe8f2000-fe8f27ff irq:47
               *-disk:0 UNCLAIMED
                    description: ATA Disk
                    product: WDC WD5000AAKS-0
                    vendor: Western Digital
                    physical id: 0
                    bus info: scsi@0:0.0.0
                    version: 05.0
                    serial: WD-WCAWF2891700
                    configuration: ansiversion=5
               *-disk:1 UNCLAIMED
                    description: ATA Disk
                    product: WDC WD5000AAKS-0
                    vendor: Western Digital
                    physical id: 1
                    bus info: scsi@2:0.0.0
                    version: 05.0
                    serial: WD-WCAWF2839960
                    configuration: ansiversion=5
               *-cdrom UNCLAIMED
                    description: SCSI CD-ROM
                    product: iHAS124   Y
                    vendor: ATAPI
                    physical id: 0.0.0
                    bus info: scsi@4:0.0.0
                    version: BL0V
                    capabilities: removable
                    configuration: ansiversion=5
            *-serial UNCLAIMED
                 description: SMBus
                 product: 82801JD/DO (ICH10 Family) SMBus Controller
                 vendor: Intel Corporation
                 physical id: 1f.3
                 bus info: pci@0000:00:1f.3
                 version: 02
                 width: 64 bits
                 clock: 33MHz
                 configuration: latency=0
                 resources: iomemory:fe8f3000-fe8f30ff ioport:400(size=32) irq:15
      *-battery
           description: Nickel Cadmium Battery
           product: Nikon Ultra Plus
           vendor: Nikon Battery
           physical id: 1
           version: 08/11/97
           serial: NI00123
           slot: Left side of System
      *-power UNCLAIMED
           description: To Be Filled By O.E.M.
           product: To Be Filled By O.E.M.
           vendor: To Be Filled By O.E.M.
           physical id: 2
           version: To Be Filled By O.E.M.
           serial: To Be Filled By O.E.M.
           capacity: 32768mWh

RESULTS.txt

                      Boot Info Script 0.61      [1 April 2012]
    
    
    ============================= Boot Info Summary: ===============================
    
    
    ============================ Drive/Partition Info: =============================
    
    no valid partition table found
    "blkid" output: ________________________________________________________________
    
    Device           UUID                                   TYPE       LABEL
    
    
    ================================ Mount points: =================================
    
    Device           Mount_Point              Type       Options
    
    /dev/mapper/isw_bhibhcjiba_Volume01 /                        ext4       (rw,errors=remount-ro,user_xattr)
    /dev/shm         /run/shm                 none       (rw,bind)
    
    
    =============================== StdErr Messages: ===============================
    
    ERROR: mkdir /var/lock/dmraid
    ERROR: mkdir /var/lock/dmraid
    ERROR: mkdir /var/lock/dmraid
      /var/lock/lvm: mkdir failed: No such file or directory
      File-based locking initialisation failed.
    mdadm: Devices UUID-ad6f745e:e3ae0039:235d131b:a9b94c7c and UUID-ad6f745e:e3ae0039:235d131b:a9b94c7c have the same name: /dev/md/Volume0
    mdadm: Duplicate MD device names in conf file were found.
    cat: /tmp/BootInfo-n8B9zWVa/BLKID_summary: No such file or directory

it had some errors, so I re-ran it from xterm inside the Live CD.
RESULTS.txt

                      Boot Info Script 0.61      [1 April 2012]
    
    
    ============================= Boot Info Summary: ===============================
    
     => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
        same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
     => Grub Legacy (v0.97) is installed in the MBR of 
        /dev/mapper/isw_bhibhcjiba_Volume0 and looks on the same drive in 
        partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
    
    sda1: __________________________________________________________________________
    
        File system:       
        Boot sector type:  Unknown
        Boot sector info: 
        Mounting failed:   mount: unknown filesystem type ''
    
    sda2: __________________________________________________________________________
    
        File system:       Extended Partition
        Boot sector type:  Unknown
        Boot sector info: 
    
    sda5: __________________________________________________________________________
    
        File system:       
        Boot sector type:  Unknown
        Boot sector info: 
        Mounting failed:   mount: unknown filesystem type ''
    mount: unknown filesystem type ''
    
    isw_bhibhcjiba_Volume01: _______________________________________________________
    
        File system:       
        Boot sector type:  Unknown
        Boot sector info: 
        Mounting failed:   mount: unknown filesystem type ''
    mount: unknown filesystem type ''
    mount: unknown filesystem type ''
    
    isw_bhibhcjiba_Volume02: _______________________________________________________
    
        File system:       Extended Partition
        Boot sector type:  Unknown
        Boot sector info: 
    
    isw_bhibhcjiba_Volume05: _______________________________________________________
    
        File system:       
        Boot sector type:  Unknown
        Boot sector info: 
        Mounting failed:   mount: unknown filesystem type ''
    mount: unknown filesystem type ''
    mount: unknown filesystem type ''
    mount: unknown filesystem type ''
    
    ============================ Drive/Partition Info: =============================
    
    Drive: sda _____________________________________________________________________
    
    Disk /dev/sda: 500.1 GB, 500107862016 bytes
    255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
    
    /dev/sda1                  63   937,151,774   937,151,712  83 Linux
    /dev/sda2         937,151,775   976,751,999    39,600,225   5 Extended
    /dev/sda5         937,151,838   976,751,999    39,600,162  82 Linux swap / Solaris
    
    
    Drive: isw_bhibhcjiba_Volume0 _____________________________________________________________________
    
    Disk /dev/mapper/isw_bhibhcjiba_Volume0: 500.1 GB, 500104826880 bytes
    255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
    
    /dev/mapper/isw_bhibhcjiba_Volume01                 63   937,151,774   937,151,712  83 Linux
    /dev/mapper/isw_bhibhcjiba_Volume02        937,151,775   976,751,999    39,600,225   5 Extended
    /dev/mapper/isw_bhibhcjiba_Volume05        937,151,838   976,751,999    39,600,162  82 Linux swap / Solaris
    
    
    "blkid" output: ________________________________________________________________
    
    Device           UUID                                   TYPE       LABEL
    
    /dev/loop0                                              squashfs   
    /dev/mapper/isw_bhibhcjiba_Volume0p1 e18d4cf9-3acc-4d67-92aa-1602b2dba3fb   ext4       
    /dev/mapper/isw_bhibhcjiba_Volume0p5 15675782-b581-4ce8-8dd6-419cfb0a30ca   swap       
    /dev/sda                                                isw_raid_member 
    /dev/sdb                                                isw_raid_member 
    /dev/sr0                                                iso9660    Ubuntu 12.04.2 LTS i386
    
    ========================= "ls -R /dev/mapper/" output: =========================
    
    /dev/mapper:
    control
    isw_bhibhcjiba_Volume0
    isw_bhibhcjiba_Volume0p1
    isw_bhibhcjiba_Volume0p2
    isw_bhibhcjiba_Volume0p5
    
    ================================ Mount points: =================================
    
    Device           Mount_Point              Type       Options
    
    /dev/loop0       /rofs                    squashfs   (ro,noatime)
    /dev/mapper/isw_bhibhcjiba_Volume0p1 /media/e18d4cf9-3acc-4d67-92aa-1602b2dba3fb ext4       (rw,nosuid,nodev,uhelper=udisks)
    /dev/sr0         /cdrom                   iso9660    (ro,noatime)
    
    
    ======================== Unknown MBRs/Boot Sectors/etc: ========================
    
    Unknown BootLoader on sda1
    
    
    Unknown BootLoader on sda2
    
    
    Unknown BootLoader on sda5
    
    
    Unknown BootLoader on isw_bhibhcjiba_Volume01
    
    
    Unknown BootLoader on isw_bhibhcjiba_Volume02
    
    
    Unknown BootLoader on isw_bhibhcjiba_Volume05
    
    
    
    =============================== StdErr Messages: ===============================
    
    hexdump: /dev/sda1: No such file or directory
    hexdump: /dev/sda1: No such file or directory
    hexdump: /dev/sda2: No such file or directory
    hexdump: /dev/sda2: No such file or directory
    hexdump: /dev/sda5: No such file or directory
    hexdump: /dev/sda5: No such file or directory
    hexdump: /dev/mapper/isw_bhibhcjiba_Volume01: No such file or directory
    hexdump: /dev/mapper/isw_bhibhcjiba_Volume01: No such file or directory
    hexdump: /dev/mapper/isw_bhibhcjiba_Volume02: No such file or directory
    hexdump: /dev/mapper/isw_bhibhcjiba_Volume02: No such file or directory
    hexdump: /dev/mapper/isw_bhibhcjiba_Volume05: No such file or directory
    hexdump: /dev/mapper/isw_bhibhcjiba_Volume05: No such file or directory

I'm still stuck.  I still have no idea what to do.  Hopefully, someone who does will see this and give me a clue.

---

