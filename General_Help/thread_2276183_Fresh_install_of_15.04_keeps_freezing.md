---
title: "Fresh install of 15.04 keeps freezing"
date: 2015-04-30
forum: General Help
---

### Post by jerry48 on 2015-04-30
I installed Ubuntu 15.04 to a separate hard drive from a flash drive and with in 30 seconds to a couple of minutes it will completely freeze and sometimes my monitor will display a bunch of random lines and colors dianonal.

---

### Post by sandyd on 2015-04-30
Hi, can you boot to the system using USB, and run the following command using the terminal.

The Terminal can be launched by clicking on the Unity Dash (Upper left button) and typing in 'terminal'
```

sudo lshw
```

Please post the output of the command in [CODE] tags after the command has finished running.

Thanks!.

---

### Post by RobGoss on 2015-04-30
Sounds like the distribution you installed might be a bit much for your machine, What are the specs for the computer in question.

---

### Post by jerry48 on 2015-04-30
Here is the output:
```

USB                       
ubuntu             
    description: Computer
    width: 64 bits
    capabilities: smbios-2.6 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 3700MiB
     *-cpu
          product: AMD Athlon(tm) II X2 250u Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          size: 1400MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save vmmcall cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:4f00(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:dfe7f000-dfe7ffff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 3.19.0-15-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 3.19
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
           *-usb:0
                description: Keyboard
                product: 2.4GHz 2way RF Receiver
                physical id: 1
                bus info: usb@2:1
                version: 2.00
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=46mA speed=12Mbit/s
           *-usb:1
                description: Keyboard
                product: USB Keyboard
                physical id: 3
                bus info: usb@2:3
                version: 3.10
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dfe7ec00-dfe7ecff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 3.19.0-15-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 3.19
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb:0
                description: Mass storage device
                product: Mass Storage Device
                vendor: Generic
                physical id: 5
                bus info: usb@1:5
                logical name: scsi6
                version: 1.00
                serial: 00000000000006
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
              *-disk:0
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sdc
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:1
                   description: SCSI Disk
                   physical id: 0.0.1
                   bus info: scsi@6:0.0.1
                   logical name: /dev/sdd
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:2
                   description: SCSI Disk
                   physical id: 0.0.2
                   bus info: scsi@6:0.0.2
                   logical name: /dev/sde
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:3
                   description: SCSI Disk
                   physical id: 0.0.3
                   bus info: scsi@6:0.0.3
                   logical name: /dev/sdf
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:4
                   description: SCSI Disk
                   physical id: 0.0.4
                   bus info: scsi@6:0.0.4
                   logical name: /dev/sdg
                   configuration: logicalsectorsize=512 sectorsize=512
           *-usb:1
                description: Mass storage device
                product: Cruzer Edge
                vendor: SanDisk
                physical id: a
                bus info: usb@1:a
                version: 1.26
                serial: 200443188011438368D6
                capabilities: usb-2.00 scsi
                configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: memory:dff00000-dfffffff
        *-network
             description: Wireless interface
             product: RT2561/RT61 802.11g PCI
             vendor: Ralink corp.
             physical id: 6
             bus info: pci@0000:01:06.0
             logical name: wlan0
             version: 00
             serial: 78:44:76:b6:cd:b9
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt61pci driverversion=3.19.0-15-generic firmware=0.8 latency=64 link=no multicast=yes wireless=IEEE 802.11bg
             resources: irq:19 memory:dfff8000-dfffffff
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:dfe78000-dfe7bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 44:87:fc:6b:99:b8
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:27 memory:dfe7d000-dfe7dfff ioport:e480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:e400(size=8) ioport:e080(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d880(size=16) memory:dfe7c000-dfe7cfff
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=16) memory:dfe77000-dfe77fff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:22 memory:de000000-deffffff memory:c0000000-cfffffff memory:dd000000-ddffffff memory:dfe40000-dfe5ffff
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: e
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3750528AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: CC44
             serial: 6VP373MV
             size: 698GiB (750GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=93fdf96d
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 797639ef-5c97-4a74-ac87-86efd7ab47c3
                size: 694GiB
                capacity: 694GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-04-28 11:46:57 filesystem=ext4 lastmountpoint=/ modified=2015-04-30 16:35:54 mounted=2015-04-30 16:35:54 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 3837MiB
                capacity: 3837MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3837MiB
                   capabilities: nofs
     *-scsi:1
          physical id: f
          logical name: scsi5
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EZEX-08M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             version: 1A01
             serial: WD-WCC3FFJ572FH
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=54768b54
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: c18e-68f0
                size: 11GiB
                capacity: 12GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-01-29 00:02:28 filesystem=ntfs label=PQSERVICE state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: c760-9550
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-01-29 00:02:30 filesystem=ntfs label=SYSTEM RESERVED state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@5:0.0.0,3
                logical name: /dev/sdb3
                version: 3.1
                serial: b671db8b-5ad8-6249-acdd-26aea82c1776
                size: 686GiB
                capacity: 686GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-11-26 02:08:22 filesystem=ntfs label=eMachines state=clean
     *-scsi:2
          physical id: 10
          bus info: usb@1:10
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdh
             size: 7633MiB (8004MB)
             capabilities: partitioned partitioned:dos
             configuration: logicalsectorsize=512 sectorsize=512 signature=00019882
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdh1
                logical name: /cdrom
                version: FAT32
                serial: 684d-d8f2
                size: 7630MiB
                capacity: 7632MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=UBUNTU 15_0 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted



```

---

### Post by sandyd on 2015-04-30
Possibly some kind of bug:

Another user's same experience: [http://ubuntuforums.org/showthread.php?t=2148832](http://ubuntuforums.org/showthread.php?t=2148832)

Try this:
Press Control + ALT+ F1 on boot and login.

You need to be connected via ethernet cable, or else you will have to configure the wireless through CLI.

Then run
```

sudo apt-get install nvidia-304
```

The above should install the nvidia proprietary drivers for your card, which might do a bit better.

---

### Post by jerry48 on 2015-05-01
How do I configure wireless through CLl?

---

### Post by sandyd on 2015-05-01
See [http://askubuntu.com/questions/330026/configure-connect-wireless-network-through-the-command-line-in-ubuntu-12-04](http://askubuntu.com/questions/330026/configure-connect-wireless-network-through-the-command-line-in-ubuntu-12-04)

You can also download the nvidia packages and install them:

[LIST=1]
[*]Boot to USB, and log onto wifi
[*]Run the following command ```
mkdir nvidia-drivers && cd nvidia-drivers && apt-get --print-uris --yes install nvidia-304 | grep ^\' | cut -d\' -f2 >downloads.list
```
[*]Run the following command ```
wget --input-file downloads.list
```
[*]Wait for it to download
[/LIST]

You should now have a folder called nvidia-drivers with the packages you need.

We can then transfer them to the Ubuntu partition so that we can install them when we go back to the installation.

```

sudo fdisk -l
``` should show your partition, you just need to mount it and place the folder inside the mounted folder.

If your not sure what to do, post the output of the command above, and we can go from there.

---

### Post by jerry48 on 2015-05-01
ok im not sure what to after the last command.

Here is the output:
```

Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x93fdf96d

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1457287167 1457285120 694.9G 83 Linux
/dev/sda2       1457289214 1465147391    7858178   3.8G  5 Extended
/dev/sda5       1457289216 1465147391    7858176   3.8G 82 Linux swap / Solaris

Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x54768b54

Device     Boot    Start        End    Sectors   Size Id Type
/dev/sdb1           2048   25167871   25165824    12G 27 Hidden NTFS WinRE
/dev/sdb2  *    25167872   25372671     204800   100M  7 HPFS/NTFS/exFAT
/dev/sdb3       25372672 1465145343 1439772672 686.6G  7 HPFS/NTFS/exFAT

Disk /dev/sdh: 7.5 GiB, 8004304896 bytes, 15633408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00019882

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdh1  *     2048 15633407 15631360  7.5G  c W95 FAT32 (LBA)



```

---

### Post by jerry48 on 2015-05-02
It runs perfect off the usb.

---

### Post by jerry48 on 2015-05-02
It runs perfect off the usb.

---

### Post by sandyd on 2015-05-03
This should mount your Ubuntu partition

```

cd
mkdir mount
sudo mount /dev/sda1 mount

```

Lets copy the files needed for nvidia installation over
```

sudo cp -R nvidia-drivers mount/opt/nvidia-drivers
```

Reboot back into your system, login and type the following
```

sudo dpkg -i /opt/nvidia-drivers/*.deb
```

Do a reboot after all of that.

---

