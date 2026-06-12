---
title: "Please help with total system lockup related to torrent apps"
date: 2008-01-15
forum: General Help
---

### Post by AstarothCY on 2008-01-15
I am experiencing a total system lockup where i cannot move the cursor and if any music is playing, it locks up as well. Hard reset is required and during bootup Ubuntu is apparently "recovering journal" for /home. The lock-ups only occur if Azureus or Deluge is running. I have had over a day of uptime without any torrent app open and there was no crashing. 

This problem started occurring pretty much out of the blue a week or so ago. I did not change anything on my system other than installing the regular updates in the normal way. I don't remember exactly when the crashing started. The crashing does not occur with any regularity, as long as a torrenting app is open, it will eventually freeze. It could take anywhere from 5 seconds to 5 hours. Since the crash is so hard, there are no error messages at all and nothing whatsoever shows up in any logs.

Not sure whether this is relevant but my wifi connection sometimes gets dropped for no reason and requires me to reconnect to the network even though it thinks it's still connected (this does not happen in windows or for anyone else in my house). Again this happens with no regularity, it could go days without happening and then it could be happening literally once every 2 minutes for a whole day.

Another minor issue is that Firefox is very sluggish, even after disabling all plugins, basically if a tab is loading something then all the other tabs are extremely slow and there is a lot of processor usage. If nothing is loading there is no problem really. Firefox runs just fine in Windows.


So anyway, here's some spec info:

Fujitsu-Siemens Scenic-P320 desktop pc
Fujitsu-Siemens D1961 mobo with SiS 661FX chipset.
Intel P4 2.93 Ghz
ATI Radeon 9550 AGP (running restricted drivers)
Soundblaster Audigy (onboard soundcard is disabled)
Zyxel G-260 USB wifi module running on ndiswrapper
Logitech LX500 wireless desktop
running Ubuntu Gutsy 32bit, and the apps i have running all the time are Firefox, Pidgin, gDesklets, Amarok and (if possible) either Azureus or Deluge. Ony Azureus is currently installed. Compiz is disabled.

/root, /home and swap are all on a 500GB Western Digital SATA disk. 
/root is a 50GB ext3 partition with 19GB free
/home is a 450GB(ish) ext3 partition with 36GB free. Torrents are downloaded onto this partition. All my media is also on this partition so I play music and videos off it. None of my torrents are big enough to cause me to worry about free space, and anyway I have it set to pre-allocate the space required. The largest torrent I had was 9GB and I suspected it so I removed it but I still get crashing. My largest torrent is now a few hundred MB.


This crashing problem is very frustrating as I essentially can't run any torrent app, and I am also worried about whether my hard disk has been damaged by all this frequent locking up. I would have somewhere to start if I had anything in my logs but I'm completely in the dark here. It would also be nice to solve the wifi module problem but it really is secondary. Any help will be hugely appreciated. Thanks.

---

### Post by ubunyou on 2008-01-16
I am having a similar problem with Azureus on Ubuntu Gutsy Gibbons install.
The system was stable until Sunday Jan 13, 2008, which is when I installed Azureus using synaptec.

I have seen two system crashes, both times I leave Azureus running overnight and wake up to a kernel panic (i.e., no more Gnome or console, no way to gracefully restart, lights flashing on my keyboard). When azureus is not running the system seems stable.

I am also using wireless only (thank you ignorant neighbor guy ;) and have some intermittent connectivity issues, This may not be the issue but thought I should mention it. 

My wireless card is a Trendnet TEW-421PC using ndiswrapper with the Win2000 drivers (the XP drivers wouldn't work). This card uses the Realtek 8185 chipset.

Another peculiar aspect of my setup is that Azureus is reading/writing from a shared NTFS partitiion. I don't think this is the problem as AstarothCY is reading/writing from an ext3 partition.

I have a whack of free space so that isn't the issue either.

Rather than provide a smattering of info I'll wait for specific requests. In the meantime if someone could point me to some relevent log files I could try to figure it out myself.

any help, as always, greatly appreciated!

What the hell i'll provide a smattering of info, here goes:

root@kyle-ubuntu:~# uname -a
Linux kyle-ubuntu 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
root@kyle-ubuntu:~# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
root@kyle-ubuntu:~# dpkg-query --status azureus
Package: azureus
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 7916
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 2.5.0.4-1ubuntu3~gutsy1
Depends: icedtea-java7-jre | sun-java6-jre | sun-java5-jre, libcommons-cli-java, liblog4j1.2-java, libseda-java, libswt3.2-gtk-java
Description: BitTorrent client
 BitTorrent is a peer-to-peer file distribution tool.
 .
 Azureus offers multiple torrent downloads, queuing/priority systems
 (on torrents and files), start/stop seeding options and instant
 access to numerous pieces of information about your torrents. Azureus
 now features an embedded tracker easily set up and ready to use.
Original-Maintainer: Shaun Jackman <sjackman@debian.org>
root@kyle-ubuntu:~#                                                                    


oot@kyle-ubuntu:~# lshw
kyle-ubuntu
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=0051598D-8DFE-D511-A8F9-001D6056E606
  *-core
       description: Motherboard
       product: P5KPL-VM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.xx
       serial: MS6C79B31004010
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0201 (08/06/2007)
          size: 64KB
          capacity: 960KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: Socket 775
          size: 2331MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KB
             capacity: 64KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MB
             capacity: 4MB
             capabilities: internal write-back instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM A1
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM B1
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8500 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: 00:1d:60:56:e6:06
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
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
           *-network
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:04:01.0
                logical name: wlan0
                version: 20
                serial: 00:14:d1:34:e5:53
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.45+Realtek,01/29/2007,5.1096.0 ip=192.168.1.76 latency=64 link=yes maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
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
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: Maxtor 6L200R0
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BAH4
                serial: L500ZKEG
                size: 189GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 39MB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 2870MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 39GB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 147GB
                   capacity: 147GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 147GB
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: WDC WD3200AAKS-0
                vendor: ATA
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 12.0
                serial: WD-WCARW1141020
                size: 298GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 97GB
                   capabilities: primary bootable
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   capacity: 9546MB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sdb3
                   capacity: 39MB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sdb4
                   size: 191GB
                   capacity: 191GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 2870MB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 32GB
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sdb7
                      capacity: 155GB
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW SH-S183L
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

root@kyle-ubuntu:~# dmesg         
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524192) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524192
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524192
[    0.000000] On node 0 totalpages: 524192
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292513 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB7F0 checksum 0
[    0.000000] ACPI: RSDP 000FB7F0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7FFA0100, 0054 (r1 A_M_I_ OEMXSDT   8000706 MSFT       97)
[    0.000000] ACPI: FACP 7FFA0290, 00F4 (r3 A_M_I_ OEMFACP   8000706 MSFT       97)
[    0.000000] ACPI: DSDT 7FFA0440, 5F0D (r1  A0844 A0844000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7FFAE000, 0040
[    0.000000] ACPI: APIC 7FFA0390, 006C (r1 A_M_I_ OEMAPIC   8000706 MSFT       97)
[    0.000000] ACPI: MCFG 7FFA0400, 003C (r1 A_M_I_ OEMMCFG   8000706 MSFT       97)
[    0.000000] ACPI: OEMB 7FFAE040, 0080 (r1 A_M_I_ AMI_OEM   8000706 MSFT       97)
[    0.000000] ACPI: HPET 7FFA6350, 0038 (r1 A_M_I_ OEMHPET   8000706 MSFT       97)
[    0.000000] ACPI: GSCI 7FFAE0C0, 2024 (r1 A_M_I_ GMCHSCI   8000706 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] Built 1 zonelists.  Total pages: 520097
[    0.000000] Kernel command line: root=UUID=87240ce1-6a22-4d75-8f4c-717c94ea9f3c ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2331.067 MHz processor.
[   36.011714] Console: colour VGA+ 80x25
[   36.011863] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   36.012056] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.073021] Memory: 2067336k/2096768k available (2015k kernel code, 28180k reserved, 916k data, 364k init, 1179264k highmem)
[   36.073027] virtual kernel memory layout:
[   36.073028]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   36.073029]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.073030]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   36.073031]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   36.073032]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   36.073032]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   36.073033]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   36.073035] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.073060] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   36.073163] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   36.073167] hpet0: 3 64-bit timers, 14318180 Hz
[   36.154124] Calibrating delay using timer specific routine.. 4665.15 BogoMIPS (lpj=9330301)
[   36.154139] Security Framework v1.0.0 initialized
[   36.154143] SELinux:  Disabled at boot.
[   36.154152] Mount-cache hash table entries: 512
[   36.154234] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
[   36.154240] monitor/mwait feature present.
[   36.154241] using mwait in idle threads.
[   36.154244] CPU: L1 I cache: 32K, L1 D cache: 32K
[   36.154246] CPU: L2 cache: 4096K
[   36.154248] CPU: Physical Processor ID: 0
[   36.154249] CPU: Processor Core ID: 0
[   36.154251] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
[   36.154257] Compat vDSO mapped to ffffe000.
[   36.154266] Checking 'hlt' instruction... OK.
[   36.170190] SMP alternatives: switching to UP code
[   36.170493] Early unpacking initramfs... done
[   36.403566] ACPI: Core revision 20070126
[   36.403599] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   36.405488] CPU0: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[   36.405499] SMP alternatives: switching to SMP code
[   36.405544] Booting processor 1/1 eip 3000
[   36.415839] Initializing CPU#1
[   36.493889] Calibrating delay using timer specific routine.. 4661.98 BogoMIPS (lpj=9323965)
[   36.493893] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
[   36.493897] monitor/mwait feature present.
[   36.493899] CPU: L1 I cache: 32K, L1 D cache: 32K
[   36.493900] CPU: L2 cache: 4096K
[   36.493901] CPU: Physical Processor ID: 0
[   36.493903] CPU: Processor Core ID: 1
[   36.493904] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
[   36.494486] CPU1: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[   36.494501] Total of 2 processors activated (9327.13 BogoMIPS).
[   36.494637] ENABLING IO-APIC IRQs
[   36.494795] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   36.641848] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   36.661846] Brought up 2 CPUs
[   36.722166] migration_cost=18
[   36.722254] Booting paravirtualized kernel on bare hardware
[   36.722300] Time: 20:01:39  Date: 00/15/108
[   36.722313] NET: Registered protocol family 16
[   36.722369] EISA bus registered
[   36.722372] ACPI: bus type pci registered
[   36.722472] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   36.722474] PCI: Using configuration type 1
[   36.722475] Setting up standard PCI resources
[   36.725046] ACPI: EC: Look up EC in DSDT
[   36.728056] ACPI: Interpreter enabled
[   36.728058] ACPI: (supports S0 S1 S3 S4 S5)
[   36.728071] ACPI: Using IOAPIC for interrupt routing
[   36.733980] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.733991] PCI: Probing PCI hardware (bus 00)
[   36.734390] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   36.734393] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   36.734853] PCI: Transparent bridge - 0000:00:1e.0
[   36.734893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.734992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   36.735070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   36.735132] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   36.741539] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   36.741630] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   36.741719] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   36.741829] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   36.741919] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.742010] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.742098] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.742186] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   36.742263] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.742270] pnp: PnP ACPI init
[   36.742275] ACPI: bus type pnp registered
[   36.745172] pnp: PnP ACPI: found 18 devices
[   36.745174] ACPI: ACPI bus type pnp unregistered
[   36.745177] PnPBIOS: Disabled by ACPI PNP
[   36.745208] PCI: Using ACPI for IRQ routing
[   36.745210] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.751285] NET: Registered protocol family 8
[   36.751286] NET: Registered protocol family 20
[   36.751319] pnp: 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   36.751325] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[   36.751328] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   36.751330] pnp: 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   36.751335] pnp: 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[   36.751338] pnp: 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   36.751340] pnp: 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   36.751345] pnp: 00:10: iomem range 0xf0000000-0xf3ffffff has been reserved
[   36.751349] pnp: 00:11: iomem range 0x0-0x9ffff could not be reserved
[   36.751351] pnp: 00:11: iomem range 0xc0000-0xcffff could not be reserved
[   36.751353] pnp: 00:11: iomem range 0xe0000-0xfffff could not be reserved
[   36.751355] pnp: 00:11: iomem range 0x100000-0x7fffffff could not be reserved
[   36.753715] Time: tsc clocksource has been installed.
[   36.753720] Switched to high resolution mode on CPU 0
[   36.753779] Switched to high resolution mode on CPU 1
[   36.781530] PCI: Bridge: 0000:00:01.0
[   36.781532]   IO window: d000-dfff
[   36.781535]   MEM window: fa000000-fe9fffff
[   36.781537]   PREFETCH window: e0000000-efffffff
[   36.781540] PCI: Bridge: 0000:00:1c.0
[   36.781540]   IO window: disabled.
[   36.781544]   MEM window: disabled.
[   36.781546]   PREFETCH window: disabled.
[   36.781550] PCI: Bridge: 0000:00:1c.1
[   36.781550]   IO window: disabled.
[   36.781554]   MEM window: fea00000-feafffff
[   36.781557]   PREFETCH window: disabled.
[   36.781560] PCI: Bridge: 0000:00:1e.0
[   36.781562]   IO window: e000-efff
[   36.781566]   MEM window: feb00000-febfffff
[   36.781568]   PREFETCH window: disabled.
[   36.781578] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.781582] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   36.781594] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.781598] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   36.781611] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   36.781615] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   36.781623] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   36.781630] NET: Registered protocol family 2
[   36.829659] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   36.829692] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   36.830141] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   36.830289] TCP: Hash tables configured (established 131072 bind 65536)
[   36.830291] TCP reno registered
[   36.845728] checking if image is initramfs... it is
[   37.305868] Freeing initrd memory: 7058k freed
[   37.306253] audit: initializing netlink socket (disabled)
[   37.306263] audit(1200427299.056:1): initialized
[   37.306323] highmem bounce pool size: 64 pages
[   37.307571] VFS: Disk quotas dquot_6.5.1
[   37.307600] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.307656] io scheduler noop registered
[   37.307657] io scheduler anticipatory registered
[   37.307659] io scheduler deadline registered
[   37.307668] io scheduler cfq registered (default)
[   37.307742] Boot video device is 0000:01:00.0
[   37.307792] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   37.307816] assign_interrupt_mode Found MSI capability
[   37.307818] Allocate Port Service[0000:00:01.0:pcie00]
[   37.307868] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   37.307899] assign_interrupt_mode Found MSI capability
[   37.307900] Allocate Port Service[0000:00:1c.0:pcie00]
[   37.307920] Allocate Port Service[0000:00:1c.0:pcie02]
[   37.307975] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   37.308006] assign_interrupt_mode Found MSI capability
[   37.308007] Allocate Port Service[0000:00:1c.1:pcie00]
[   37.308028] Allocate Port Service[0000:00:1c.1:pcie02]
[   37.308122] isapnp: Scanning for PnP cards...
[   37.660700] isapnp: No Plug & Play device found
[   37.673984] Real Time Clock Driver v1.12ac
[   37.674105] hpet_resources: 0xfed00000 is busy
[   37.674134] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.674214] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.674671] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.675062] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.675144] input: Macintosh mouse button emulation as /class/input/input0
[   37.675197] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   37.677187] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.677190] serio: i8042 AUX port at 0x60,0x64 irq 12
[   37.677343] mice: PS/2 mouse device common for all mice
[   37.677400] EISA: Probing bus 0 at eisa.0
[   37.677424] EISA: Detected 0 cards.
[   37.677477] TCP cubic registered
[   37.677485] NET: Registered protocol family 1
[   37.677498] Using IPI No-Shortcut mode
[   37.677594]   Magic number: 8:179:43
[   37.677597]   hash matches device ttyec
[   37.677632]   hash matches device 00:0f
[   37.677748] Freeing unused kernel memory: 364k freed
[   37.694554] input: AT Translated Set 2 keyboard as /class/input/input1
[   38.816658] AppArmor: AppArmor initialized<5>audit(1200427300.556:2):  type=1505 info="AppArmor initialized" pid=1231
[   38.821993] fuse init (API version 7.8)
[   38.824994] Failure registering capabilities with primary security module.
[   38.850300] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  DA, should be D5 [20070126]
[   38.850309] ACPI: SSDT 7FFB00F0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[   38.850740] ACPI: SSDT 7FFB02D0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[   38.851036] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   38.851043] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.132318] usbcore: registered new interface driver usbfs
[   39.132334] usbcore: registered new interface driver hub
[   39.139567] usbcore: registered new device driver usb
[   39.140076] USB Universal Host Controller Interface driver v3.0
[   39.140115] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   39.140123] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   39.140125] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   39.140205] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   39.140228] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000c480
[   39.140297] usb usb1: configuration #1 chosen from 1 choice
[   39.140316] hub 1-0:1.0: USB hub found
[   39.140320] hub 1-0:1.0: 2 ports detected
[   39.156125] SCSI subsystem initialized
[   39.159455] libata version 2.21 loaded.
[   39.244227] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   39.244235] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   39.244238] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   39.244323] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   39.244345] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[   39.244551] usb usb2: configuration #1 chosen from 1 choice
[   39.244640] hub 2-0:1.0: USB hub found
[   39.244644] hub 2-0:1.0: 2 ports detected
[   39.348136] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   39.348141] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   39.348144] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   39.348233] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   39.348254] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000c880
[   39.348466] usb usb3: configuration #1 chosen from 1 choice
[   39.348563] hub 3-0:1.0: USB hub found
[   39.348567] hub 3-0:1.0: 2 ports detected
[   39.452069] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   39.452074] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   39.452077] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   39.452176] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   39.452197] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000cc00
[   39.452434] usb usb4: configuration #1 chosen from 1 choice
[   39.452542] hub 4-0:1.0: USB hub found
[   39.452548] hub 4-0:1.0: 2 ports detected
[   39.557049] ata_piix 0000:00:1f.1: version 2.11
[   39.557058] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   39.557077] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   39.557126] scsi0 : ata_piix
[   39.570095] scsi1 : ata_piix
[   39.570173] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   39.570176] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   39.733424] ata1.00: ATA-7: Maxtor 6L200R0, BAH41G10, max UDMA/133
[   39.733427] ata1.00: 398297088 sectors, multi 16: LBA48
[   39.749393] ata1.00: configured for UDMA/133
[   39.914214] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L200R0   BAH4 PQ: 0 ANSI: 5
[   39.914249] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   39.914265] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   39.914283] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   39.914301] scsi2 : ata_piix
[   39.914325] scsi3 : ata_piix
[   39.914389] ata3: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c082 bmdma 0x0001b880 irq 19
[   39.914392] ata4: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001bc02 bmdma 0x0001b888 irq 19
[   40.081957] ata3.00: ATA-8: WDC WD3200AAKS-00VYA0, 12.01B02, max UDMA/133
[   40.081960] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   40.096162] ata3.00: configured for UDMA/133
[   40.571195] ata4.00: ATAPI: TSSTcorpCD/DVDW SH-S183L, SB01, max UDMA/33
[   40.571198] ata4.00: applying bridge limits
[   40.743078] ata4.00: configured for UDMA/33
[   40.743136] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 12.0 PQ: 0 ANSI: 5
[   40.744143] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S183L SB01 PQ: 0 ANSI: 5
[   40.746166] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   40.746173] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   40.746176] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   40.746279] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   40.746300] ehci_hcd 0000:00:1d.7: debug port 1
[   40.746305] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   40.746309] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xf9ffbc00
[   40.750183] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.750397] usb usb5: configuration #1 chosen from 1 choice
[   40.750492] hub 5-0:1.0: USB hub found
[   40.750497] hub 5-0:1.0: 8 ports detected
[   40.754322] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   40.754329] sd 0:0:0:0: [sda] Write Protect is off
[   40.754331] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.754341] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.754371] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   40.754377] sd 0:0:0:0: [sda] Write Protect is off
[   40.754379] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.754389] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.754391]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   40.799421] sd 0:0:0:0: [sda] Attached SCSI disk
[   40.799456] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   40.799464] sd 2:0:0:0: [sdb] Write Protect is off
[   40.799466] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   40.799477] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.799506] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   40.799519] sd 2:0:0:0: [sdb] Write Protect is off
[   40.799520] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   40.799530] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.799533]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 sdb6 sdb7 >
[   40.844836] sd 2:0:0:0: [sdb] Attached SCSI disk
[   40.847276] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.847288] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   40.847300] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   40.864152] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   40.864155] Uniform CD-ROM driver Revision: 3.20
[   40.864282] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   41.108424] Attempting manual resume
[   41.108427] swsusp: Resume From Partition 8:2
[   41.108428] PM: Checking swsusp image.
[   41.108566] PM: Resume from disk failed.
[   41.118278] EXT3-fs: INFO: recovery required on readonly filesystem.
[   41.118280] EXT3-fs: write access will be enabled during recovery.
[   42.365052] kjournald starting.  Commit interval 5 seconds
[   42.365060] EXT3-fs: recovery complete.
[   42.365508] EXT3-fs: mounted filesystem with ordered data mode.
[   48.695900] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.697089] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.736580] intel_rng: FWH not detected
[   48.815121] parport_pc 00:06: reported by Plug and Play ACPI
[   48.815216] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   48.818645] input: PC Speaker as /class/input/input2
[   48.829614] Linux agpgart interface v0.102 (c) Dave Jones
[   49.011537] iTCO_vendor_support: vendor-support=0
[   49.012416] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   49.043468] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   49.043476] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   49.043482] atl1 0000:02:00.0: version 2.0.7
[   49.054905] nvidia: module license 'NVIDIA' taints kernel.
[   49.369481] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   49.369489] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   49.369546] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   49.494735] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   49.494746] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   49.546154] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   49.548932] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   49.548982] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   49.700618] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   49.946077] lp0: using parport0 (interrupt-driven).
[   49.963945] ndiswrapper version 1.45 loaded (smp=yes)
[   50.013290] ndiswrapper: driver net8185 (Realtek,01/29/2007,5.1096.0129.2007) loaded
[   50.013753] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.284956] ndiswrapper: using IRQ 16
[   56.619817] wlan0: ethernet device 00:14:d1:34:e5:53 using NDIS driver: net8185, version: 0x50448, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
[   56.619979] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   56.620187] usbcore: registered new interface driver ndiswrapper
[   56.669446] Adding 2939884k swap on /dev/sda2.  Priority:-1 extents:1 across:2939884k
[   57.055567] EXT3 FS on sda3, internal journal
[   58.041910] NET: Registered protocol family 17
[   58.477502] input: Power Button (FF) as /class/input/input4
[   58.477514] ACPI: Power Button (FF) [PWRF]
[   58.477590] input: Power Button (CM) as /class/input/input5
[   58.477599] ACPI: Power Button (CM) [PWRB]
[   58.485582] No dock devices found.
[   59.191226] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   59.191229] apm: disabled - APM is not SMP safe.
[   59.770573] atl1 0000:02:00.0: Unable to enable MSI: -22
[   60.147311] Failure registering capabilities with primary security module.
[   60.258296] NET: Registered protocol family 10
[   60.258360] lo: Disabled Privacy Extensions
[   60.258388] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.312004] Bluetooth: Core ver 2.11
[   60.312036] NET: Registered protocol family 31
[   60.312038] Bluetooth: HCI device and connection manager initialized
[   60.312040] Bluetooth: HCI socket layer initialized
[   60.329008] Bluetooth: L2CAP ver 2.8
[   60.329010] Bluetooth: L2CAP socket layer initialized
[   60.356871] Bluetooth: RFCOMM socket layer initialized
[   60.356878] Bluetooth: RFCOMM TTY layer initialized
[   60.356880] Bluetooth: RFCOMM ver 1.8
[   70.270141] wlan0: no IPv6 routers present
[ 1924.249687] Failure registering capabilities with primary security module.

---

### Post by ubunyou on 2008-01-16
found the logs dir - no glaring errors to report - some 404 errors but nothing else.
Tarred up the whole ~/.azureus and ~/.Azureus dirs and attached for those interested.

---

### Post by AstarothCY on 2008-01-16
bump

---

### Post by SOULRiDER on 2008-01-16
Azureus has memory leaks. Your swap starts to fill and eventually locks your system if you dont realzie in time. I suggest you use other clients. Deluge seems to be alright. Other clients like rTorrent (which is a CLI client) are lightweight and IMO better.

---

### Post by ubunyou on 2008-01-16
Hey just an update. I donwloaded Azureus 3.x from their site yesterday (not using apt-get), ran it all night, and no crashes to report. Perhaps the leaks are all patched up in the 3.x version.

---

### Post by AstarothCY on 2008-01-16
> **SOULRiDER said:**
> Azureus has memory leaks. Your swap starts to fill and eventually locks your system if you dont realzie in time. I suggest you use other clients. Deluge seems to be alright. Other clients like rTorrent (which is a CLI client) are lightweight and IMO better.

Thanks for the reply. As I said, Deluge also produced the same crash. In fact it was Deluge that was crashing first, causing me to switch to Azureus.

---

### Post by AstarothCY on 2008-01-17
bump

---

### Post by xdarkxanarchyx on 2008-01-18
I thought I was the only one with bittorrent issues. I've noticed my system actually just shuts down after a while if I'm using Ktorrent, Azureus or Deluge. I may have other problems though. Weak/faulty power supply (1 molex(IDE) connector does not work/external power cord is loose), faulty new video card (Radeon X1550 using fglrx drivers). But mostly it happens with a bittorrent client.

---

### Post by AstarothCY on 2008-01-18
it would be nice if someone with better knowledge of computers in general (not just linux) could tell us where to start debugging.. i.e. what sort of problem does this sound like and how can we do some experiments to exclude certain things?

---

### Post by ubunyou on 2008-01-23
I am still experiencing the system crashes using either of Azureus or Deluge.
Someone suggested to me that this is likely my NIC drivers, and not an error in the torrent clients. Could it be that the wireless driver crashes when torrent clients are running due to the heavy load placed on the network? Note I am using ndiswrapper to drive a RTL8185 wireless PCI NIC ... I have no wired connection.

I reduced my max connection settings but still observe crashes. 
My system info is dumped out above.
Would really appreciate some help. Can anyone out there suggest effective strategies to troubleshoot this problem?

---

### Post by AstarothCY on 2008-01-23
This sounds quite plausible to me. I'll try a wired connection to my network to see if i get the same crashes, that should confirm or eliminate your hypothesis.

[-o<

---

### Post by spina_sol on 2008-01-23
Just found this thread, and I had a similar crash last night/this morning. I left Deluge on overnight a couple times and received a Network Manager error. Then I rebooted it locked up after booting fine. I again rebooted, only this time it gave me the error: Boot Failure: System Halted.

The CD I installed from (download of Gutsy) has no rescue option, so I will try the system rescue cd referenced here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=668402](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=668402)

Any thoughts?

---

### Post by ubunyou on 2008-01-25
The boot failure system halt occurs when the bios can't read or has errors reading the Master Boot Record (MBR) on your harddrive. Thats where the computer hardware is told where to go to load the OS - without the MBR linux or any other OS won't even start.
Pretty easy to fix though you just got to mount your boot partition using the live CD and rerun grub-install <drive id> (i.e. drive id is like /dev/sda ). This assumes that you have configured grub.conf correctly - look that up somewhere.

But I really don't want this thread to get off topic - think wireless/torrent problems, not MBR corruption!!

---

### Post by submerged2go on 2008-01-25
Hello everyone, 

Just to chip in and bump the thread up, I also have this problem as well largely to do with any bit-torrent programs, I've tried Deluge (my current and standard one), Azureus, the standard Bit-Torrent client Ubuntu comes with, Ktorrent and others I can't remember off the top of my head. 

What tends to happen, with remarkable consistancy, is that if I leave the computer running for around 45 mins (with the monitor off or on, it doesn't matter) then come back to the computer and move the mouse a fraction, all of the torrents then stops their downloading/seeding, the mouse moves VERY slowly like a grandad, the internet connection is offline (somehow) and its just a right pain to nagivate with the mouse. Strangely enough, once the bit-torrent program is closed down and I revert back to keyboard shortcuts to nagivate to menus, there is not a very noticeable performance drop-off in the time it takes to open a folder. A program is a different story though. Usual course of action is to hard reboot the computer. 

It runs fine if I don't touch it after a 45 mins period though, have allowed it to run 12 hours and no problems presented, apart from in the morning when I move the mouse of course. 

One thing I have noticed is that I get a massive amount of system, kern and message log in the System Log section, all saying the same thing as soon as I have moved the mouse; 


```
[11472.582390] irq 11: nobody cared (try booting with the "irqpoll" option)
[11472.582438]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
[11472.582455]  [note_interrupt+520/576] note_interrupt+0x208/0x240
[11472.582466]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
[11472.582474]  [handle_fasteoi_irq+112/160] handle_fasteoi_irq+0x70/0xa0
[11472.582481]  [do_IRQ+64/128] do_IRQ+0x40/0x80
[11472.582488]  [profile_tick+62/128] profile_tick+0x3e/0x80
[11472.582501]  [common_interrupt+35/48] common_interrupt+0x23/0x30
[11472.582515]  [native_safe_halt+2/16] native_safe_halt+0x2/0x10
[11472.582521]  [default_idle+56/80] default_idle+0x38/0x50
[11472.582525]  [cpu_idle+28/96] cpu_idle+0x1c/0x60
[11472.582529]  [start_kernel+565/896] start_kernel+0x235/0x380
[11472.582540]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
```

I actually love the section where it says: "irq11: nobody cared"....Well, I cared! Anyway, even booting with the "irqpoll" option has not resolved that problem, only *increases* other problems that were not even there first time around. The above is from the kern.log section. The sys log also states that then it goes and repeats the following ad infinitum unless i hard reboot it. 

```

[11472.582550] handlers:
[11472.582552] [<f0900dc0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[11472.582595] [<f0900dc0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[11472.582614] Disabling IRQ #11
[11568.803923] Inbound IN=eth0 OUT= MAC=00:04:e2:5c:8c:ec:00:11:50:47:09:73:08:00 SRC=92.80.253.13 DST=192.168.88.1 LEN=1452 TOS=0x00 PREC=0x00 TTL=106 ID=20664 DF PROTO=TCP SPT=23177 DPT=45687 WINDOW=16667 RES=0x00 ACK URGP=0 

[11583.247393] Inbound IN=eth0 OUT= MAC=00:04:e2:5c:8c:ec:00:11:50:47:09:73:08:00 SRC=209.195.64.66 DST=192.168.88.1 LEN=131 TOS=0x00 PREC=0x00 TTL=107 ID=17133 PROTO=UDP SPT=17913 DPT=6881 LEN=111 

[11595.868385] Inbound IN=eth0 OUT= MAC=00:04:e2:5c:8c:ec:00:11:50:47:09:73:08:00 SRC=79.126.61.212 DST=192.168.88.1 LEN=134 TOS=0x00 PREC=0x00 TTL=110 ID=22555 PROTO=UDP SPT=11187 DPT=6881 LEN=114 

[11597.833821] Inbound IN=eth0 OUT= MAC=00:04:e2:5c:8c:ec:00:11:50:47:09:73:08:00 SRC=213.207.168.68 DST=192.168.88.1 LEN=1452 TOS=0x00 PREC=0x00 TTL=110 ID=19698 DF PROTO=TCP SPT=27201 DPT=40089 WINDOW=64179 RES=0x00 ACK URGP=0 

[11691.174487] Inbound IN=eth0 OUT= MAC=00:04:e2:5c:8c:ec:00:11:50:47:09:73:08:00 SRC=80.213.210.231 DST=192.168.88.1 LEN=1452 TOS=0x00 PREC=0x00 TTL=102 ID=39382 DF PROTO=TCP SPT=47477 DPT=54620 WINDOW=65535 RES=0x00 ACK URGP=0 

[11697.272310] Inbound IN=eth0 OUT= MAC=00:04:e2:5c:8c:ec:00:11:50:47:09:73:08:00 SRC=99.229.144.156 DST=192.168.88.1 LEN=1452 TOS=0x00 PREC=0x00 TTL=109 ID=55666 DF PROTO=TCP SPT=56310 DPT=35164 WINDOW=64315 RES=0x00 ACK URGP=0 
```

I have added spaces in to make it easier to read. Anyway, it repeats that every five seconds. 

The computer has Feisty Ubuntu in it, with Gnome and everything pretty much standard and no real changes to it, apart from NTFS reader and Amarok. I however, have changed to XFCE window manager in hope that it would not happen under a different window manager (can only try!) and it still has presented this problem. I don't mind the problem too much, but it has become a very steady irritation and a source of much annoyances and I am completely unable to find out WHAT exactly is causing this problem.  

Oh, I have a wired connection to a Belkin wireless and wired router.

So, I hope there are people out there who will help to understand this rather vexing problem for the OP and anyone else. :)

---

### Post by AstarothCY on 2008-01-26
I've been connected via ethernet instead of wifi for a few hours with Azureus running and no crash. I will let it run a bit longer and will then try connecting via wifi.

---

### Post by ubunyou on 2008-01-26
When my system crashes I sometimes see behavior similar to what submerged2go describes. The mouse becomes slow and there is 1 or 2 second delay while typing, this lasts for less than 10 seconds and then the system crashes. Sometimes the screen goes blank, other times it just freezes the current frame. Common throughout crashes is that my keyboard lights start flashing (i think that means kernel panic)

---

### Post by smbm on 2008-01-27
I think the problem is something pretty low level.

I have been running Hardy since the repos opened and was still getting the mysterious freezes until the kernel and all it's associated gubbins were upgraded.I've been torrent lock up free since then.

So I guess hold of on the torrents until Hardy is released.

Don't know if this helps any of you.

---

### Post by submerged2go on 2008-01-27
Hm, so Hardy Heron doesn't have this problem then? And you're implying that the problem is unlikely to ever be resolved for Feisty and Gusty? 

It actually does help us for the long term view, as we can eventually have a system that will not freeze while using torrent programs or heavy downloading sessions. I point out the heavy downloading sessions, as once I had to download Xubuntu from their download page through the web browser (the torrent program died that time) and left the browser open to download the 700MB or so file. After 20 mins of leaving it alone, it froze and dropped the download roughly around 35% to 45% through. 

Obviously, I wasn't a happy bunny. :(. However in my case it is not restricted to torrent programs, it seems to happen under lots of downloads during moments of inactivity then when the computer is woken up or there is activity after a while, the lock up/slowdown happens. 

I am assuming that it's something to do with the Ipv6 and/or IRQ numbers, but to test it, I haven't got the faintest how to do that....yet.

---

### Post by smbm on 2008-01-27
> **submerged2go said:**
> Hm, so Hardy Heron doesn't have this problem then? And you're implying that the problem is unlikely to ever be resolved for Feisty and Gusty? 

It actually does help us for the long term view, as we can eventually have a system that will not freeze while using torrent programs or heavy downloading sessions. I point out the heavy downloading sessions, as once I had to download Xubuntu from their download page through the web browser (the torrent program died that time) and left the browser open to download the 700MB or so file. After 20 mins of leaving it alone, it froze and dropped the download roughly around 35% to 45% through. 

Obviously, I wasn't a happy bunny. :(. However in my case it is not restricted to torrent programs, it seems to happen under lots of downloads during moments of inactivity then when the computer is woken up or there is activity after a while, the lock up/slowdown happens. 

I am assuming that it's something to do with the Ipv6 and/or IRQ numbers, but to test it, I haven't got the faintest how to do that....yet.

I doubt it will be fixed in Feisty or Gutsy as I think the problem might lie in the kernel.

I guess if you're reasonably competent you could try [[COLOR="DarkOrange"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=646755") although it's probably not for the faint of heart.

I can pretty much rule out IPv6 too as I have blacklisted that module here.

Good luck.

---

### Post by AstarothCY on 2008-02-02
Sorry it took me ages to update this.

The problem is clearly related to the wireless. I had a WEEK of uptime and heavy torrenting on wired lan with no crashes whatsoever. I then connected the wireless, loaded up some torrents, and within minutes i had a crash. I rebooted, connected with wired lan, no crash.

What's the next step?

---

### Post by smbm on 2008-02-02
The problem is not present in the testing version of Hardy so I would recommend that you wait for Hardy to come out.

---

### Post by ubunyou on 2008-02-02
I upgraded my kernel to Hardy and no longer observe any crashes.
My wireless is still 'messed' but it no longer causes system lock ups when torrent clients are running. Thanks to smbm for the relevant suggestion.

As a workaround for the wireless problem i wrote a script to cycle the wireless by reloading the ndiswrapper module and then bringing the interface back up and that has been working for me so far. Script below for those interested. Not a great solution but it works so far.


Save the script somewhere and make it executable. I have it in /usr/scripts/reload_wireless.pl. All you have to change is the <INSERT ESSID HERE> to whatever your ESSID is for your network.

#!/usr/bin/perl
use strict;
use warnings;
use DateTime;

my $dt = DateTime->now;

open LOG, '>>', "/usr/scripts/reload_wireless.out"
        or die "Couldn't open log for write";

my $scan = `iwlist wlan0 scan 2>&1`;
my $isup = ($scan =~ m/ESSID:"**<INSERT ESSID HERE>**"\s*$/m) ? 1 : 0;

if(!$isup) {
                print LOG "$dt Wireless Down\n";
                print LOG "Disabling wireless\n",`ifdown wlan0 2>&1`;
                print LOG "Reloading ndiswrapper\n";
                print LOG `modprobe -r ndiswrapper 2>&1`;
                print LOG `modprobe ndiswrapper 2>&1`;
                print LOG "Cycling connection via if[up|down]\n";
                print LOG `ifdown wlan0 2>&1`;
                print LOG `ifup wlan0 2>&1`;
}
else {
                print LOG "$dt Wireless Up\n";
}

close LOG or die "Couldn't close log";

So save this somewhere, make it executable, login as root (sudo -s),then add to crontab (using crontab -e) and add the following entry:

# m h  dom mon dow   command
*/5 * * * * /usr/scripts/reload_wireless.pl

Actually you'd probably also have to use CPAN to get the DateTime package used by the script ...
> cpan
install DateTime
hit yes a couple times

UPDATE:
I stopped using this script for a while.
-The crashes went away using the newest hardy kernel.
If you set the apt sources according to instructions from smbm's linked post you can upgrade.
-Wireless still goes down every 30-45 minutes or so, trying to come up with a better fix ... the script above is kinda busted but i got no time to fix for now.  Will update if/when i got it sorted.

UPDATE:
All my problems stemmed from my Trendnet TEW-421PC wireless card. After smashing and replacing with a linksys WMP54G all is golden. Yay linksys (with realtek chipset), boo trendnet (with realtek chipset ... ?)

---

### Post by AstarothCY on 2008-02-02
Forgive my noobishness but what exactly does that script do? does it automatically revive your connection if it goes down?

I won't be upgrading to the Hardy kernel, I think I will just wait for Hardy to come out and do a fresh install. In the meantime i'll just connect wired.

---

### Post by submerged2go on 2008-02-04
Astaroth, I'm surprised that merely connecting to the wired lan meant that you had no crashes. Do you mean that you connected to a proper wired router or just connected an ethernet to a wireless router that has ethernet ports at the back? 

I have only got a wired connection on my computer and it still does the same if I leave it running for 45 mins on its own. I did upgrade to Gusty as I was bored one day, through the internet. It was around 75% when I accidently moved the mouse while it was downloading the packets to complete the installation and it then instantly stopped downloading. So I had to reboot and resume installation...

I have been debating about putting on Hardy but at the moment haven't quite got the confidence yet. Plus, it's not too bad a problem yet.

And yes, I would like to know what the code means and how it does it ubunyou :)

---

### Post by smbm on 2008-02-04
> **submerged2go said:**
> Astaroth, I'm surprised that merely connecting to the wired lan meant that you had no crashes. Do you mean that you connected to a proper wired router or just connected an ethernet to a wireless router that has ethernet ports at the back? 

I have only got a wired connection on my computer and it still does the same if I leave it running for 45 mins on its own. I did upgrade to Gusty as I was bored one day, through the internet. It was around 75% when I accidently moved the mouse while it was downloading the packets to complete the installation and it then instantly stopped downloading. So I had to reboot and resume installation...

I have been debating about putting on Hardy but at the moment haven't quite got the confidence yet. Plus, it's not too bad a problem yet.

And yes, I would like to know what the code means and how it does it ubunyou :)

You could try [[COLOR="DarkOrange"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=646755"). It's probably not quite as extreme as upgrading the whole system to Hardy.

---

### Post by ubunyou on 2008-02-05
So the script is written in bad perl code, and perl is sort of a love/hate thing to start with so I apologize if it makes no sense. 
Short version: it scans for wireless networks and checks if the one you want (i.e., **<INSERT ESSID HERE>**) is detected. If it is then the script exits. If it is not then it stops your wireless interface (ifdown), reloads the wireless driver (modprobe), and starts wireless again (ifup). This worked for my particular problem, but who knows if others are having the same problem as me. This will not solve crashes, it only helps if you notice your wireless goes dead (no connectivity) after a while, in some cases.

Also a note that I am tweaking the script cuz it is not always working for me. Wierd actually it works every time if i run it as root from a terminal, but it doesn't always work when it is run automatically, as root, from cron.

BTW cron is a system daemon (something running in the background) that will periodically execute commands for you. I set this script to run every 5 minutes. 

Hope this helps.

Those interested in perl read on:

> **ubunyou said:**
> 
#!/usr/bin/perl
use strict;
use warnings;
use DateTime;

This is just stuff you need at the top of a perl script. The #! tells bash what to use to interpret the script. The use are either settings or modules that perl needs for this script.


> **ubunyou said:**
> 
open LOG, '>>', "/usr/scripts/reload_wireless.out"
        or die "Couldn't open log for write";
close LOG or die "Couldn't close log";

This is to open and close a log file that contains result of commands.

> **ubunyou said:**
> 
my $scan = `iwlist wlan0 scan 2>&1`;
my $isup = ($scan =~ m/ESSID:"**<INSERT ESSID HERE>**"\s*$/m) ? 1 : 0;

The tricky part. 
Anything in backticks (i.e., `blahblah` gets executed as a command, so if i went:
my $var = `uname -a` then the output of the uname command is assigned to $var. For me this is (Linux kyle-ubuntu 2.6.24-5-generic #1 SMP Thu Jan 24 19:45:21 UTC 2008 i686 GNU/Linux)

So the first line assigns the output of a wireless scan to $scan
The second line is checking that a particular string 'ESSID:blahhhh....' is in the output and assigning either a 1 (the string is in the output) or a 0 (the string is not in the output) to the variable $isup. 

> **ubunyou said:**
> 
if(!$isup) {
                print LOG "$dt Wireless Down\n";
                print LOG "Disabling wireless\n",`ifdown wlan0 2>&1`;
                print LOG "Reloading ndiswrapper\n";
                print LOG `modprobe -r ndiswrapper 2>&1`;
                print LOG `modprobe ndiswrapper 2>&1`;
                print LOG "Cycling connection via if[up|down]\n";
                print LOG `ifdown wlan0 2>&1`;
                print LOG `ifup wlan0 2>&1`;
}


So if isup is 0, this will run. If it's 1, it will not run ( '!' means NOT ).
All the rest is just running system commands using backticks and logging the output.

---

### Post by AstarothCY on 2008-02-05
That is really cool. Good job! I personally won't be needing it since I'm going to just stay wired until I feel confident enough to install the Hardy kernel, but I'm sure somebody will find it useful.

BTW, submerged2go, yes all I had to do was connect to my wireless router via ethernet. I am 100% sure that this is a fix, i have had days of uptime on ethernet with no crashes at all yet I can only manage a few minutes on wlan.

---

### Post by submerged2go on 2008-02-05
Ironically, I'm connected by wired and it still does the same thing. The computer did use to have the wireless card, but I took it out after very poor performance from it due to the location of my room and thick walls and slapped it into a test computer so the computer should not have a conflict with wireless or anything. It does say its connected through wired network anyhow. 

Ubunyou, thank you for explaining the code and how it works! I found it very useful and it doesn't matter if it is "bad code" for the moment, as it works for you. :)

---

### Post by submerged2go on 2008-02-12
> **smbm said:**
> You could try [[COLOR="DarkOrange"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=646755"). It's probably not quite as extreme as upgrading the whole system to Hardy.

Well, last night I got really quite annoyed and vexed about the constant lock-ups and slowness associated with heavy download usage that I decided on that moment to upgrade without any sort of backup to the newer kernel system. 

Kinda silly I thought after I had it running rather well...

However I must say that the fact that I can let the computer download as long or as short as I like without fear of it locking up or doing anything weird is a blessed relief! Now I can download the updated versions of Ubuntu without having to worry about a thing. It actually works! 

Only problem with the new kernel is that it runs slightly slower when switching programs around in the same workspace. But that's nothing to me, so I'm very happy about it. Oh, and it did take me a while to figure out the correct graphic card and monitor sizes before I got it back to normal as it didn't initially recognise my nVidia card and set it to 800x640 rather than 1024 x 768 on the monitor without using my card....At least, that is what I understood it to say. 

Anyway, many thanks smbm for pointing me to the post with very helpful information on how to upgrade to the latest kernel! Just need to play around with it that is all...:)

---

### Post by smbm on 2008-02-12
> **submerged2go said:**
> Anyway, many thanks smbm for pointing me to the post with very helpful information on how to upgrade to the latest kernel! Just need to play around with it that is all...:)

No problem. Glad it worked and didn't break your system.

---

### Post by ttr738 on 2008-02-13
I have the same problem with my system freezing when it's downloading torrents.
Only thing is, it freezes randomly anyway so maybe that's not the problem. Just does it more when torrenting.
The weird thing is, when I use XP to do torrenting, the thing can reboot itself randomly too.

Thinking maybe this problem could be hardware related? Could it be associated with disc activity or something? Ubuntu makes my system crash a lot less than XP, and it doesn't churn the HDDs every 5 seconds, so as well as XP being a piece of **** maybe this could be something to do with it?

Can anyone give me a clue of which error log to look in and what for?
I've got no idea how to tell exactly what made my system crash, but i'm guessing linux will tell me more than XP :-)

Any help appreciated!

---

### Post by submerged2go on 2008-03-01
> **ttr738 said:**
> I have the same problem with my system freezing when it's downloading torrents.
Only thing is, it freezes randomly anyway so maybe that's not the problem. Just does it more when torrenting.
The weird thing is, when I use XP to do torrenting, the thing can reboot itself randomly too.

Thinking maybe this problem could be hardware related? Could it be associated with disc activity or something? Ubuntu makes my system crash a lot less than XP, and it doesn't churn the HDDs every 5 seconds, so as well as XP being a piece of **** maybe this could be something to do with it?

Can anyone give me a clue of which error log to look in and what for?
I've got no idea how to tell exactly what made my system crash, but i'm guessing linux will tell me more than XP :-)

Any help appreciated!

Sorry for the very long delay, I had to solve some problems with Hardy Heron kernel as it somehow went completely wrong and gave me the shell command line! Anyway, re-installed with the latest Xubuntu and everything is working fine. Well, it would do if the downloads didn't make everything crash again. It was one of the updates that did it however not yet been able to find out which one it was. 

Anyway, back to ttr's question. One of the best ways to see what is happening to your computer, is through Ubuntu's kernel and system logs. You should find them under "System Logs" or something very similar to that under Gnome. It would be found by going to Applications -> Systems -> Logs (or a variation of that). I am using XFCE and it is slightly differently laid out. The reason why I say go to the kernel and system logs in Ubuntu, is that they will allow you to see what error messages are thrown up which will enable you to have more of an idea where the problem is occurring and post it back on here with more details. 

However, as you have mentioned that Windows XP also reboots "randomly" while torrenting, it does sound more of a network problem that could be affecting the memory side of your computer. Sometimes with a lot of files, it can take up a lot of RAM memory and once it's gets overloaded, it reboots to save itself...from what I understand of the process. 

Once again, sorry for the massive delay in replying.

---

### Post by AstarothCY on 2008-03-03
> **ttr738 said:**
> I have the same problem with my system freezing when it's downloading torrents.
Only thing is, it freezes randomly anyway so maybe that's not the problem. Just does it more when torrenting.
The weird thing is, when I use XP to do torrenting, the thing can reboot itself randomly too.

Thinking maybe this problem could be hardware related? Could it be associated with disc activity or something? Ubuntu makes my system crash a lot less than XP, and it doesn't churn the HDDs every 5 seconds, so as well as XP being a piece of **** maybe this could be something to do with it?

Can anyone give me a clue of which error log to look in and what for?
I've got no idea how to tell exactly what made my system crash, but i'm guessing linux will tell me more than XP :-)

Any help appreciated!

Do you still get rebooting if you aren't torrenting? If so, there could be a more general hardware issue, like a faulty motherboard or power supply.

---

### Post by ttr738 on 2008-03-03
> **AstarothCY said:**
> Do you still get rebooting if you aren't torrenting? If so, there could be a more general hardware issue, like a faulty motherboard or power supply.

Yeah that's what I was thinking... Hence posting my experience here as it sounded pretty similar to what others were seeing, and it might not be a bug in Ubuntu at all. 
I'm going to wait until it happens again (sod's law dictates it won't be for ages!) and post some logs up here. Cheers Submerged2go for that advice too!

Which log is most likely to say what's going wrong then? I've got auth.log, daemon.log, debug, kern.log, messages, syslog, user.log and xorg.0.log to choose from...

Luckily i'm just about to go on holiday for a couple of weeks anyway, so I won't have to swear at the computer for a while :)

---

### Post by submerged2go on 2008-03-03
> **ttr738 said:**
> 
Which log is most likely to say what's going wrong then? I've got auth.log, daemon.log, debug, kern.log, messages, syslog, user.log and xorg.0.log to choose from...


Generally from my experience with torrenting and wireless troubleshooting, you want to have a look at the syslog, kern.log and the messages. Try and pinpoint the exact second when it goes wrong as in rebooting or just not working, as after you've booted it back up, it should show it up in these three logs. In extreme detail in some cases. So don't be too surprised if you see reams and reams of logs spanning five seconds! 

Anyhow, swearing at the computer (at home and when no-one's around!) is quite therapeutic I find...but not conductive to good fault finding! :)

---

### Post by Person98 on 2008-03-19
I have been having the same problem i have been using gnome torrent and azerus i am on wireless, the real bad news is i was downloading to my windows harddrive (my linux one is only 8 gigs)  and it crashed so now my windows harddrive is horribly corrupt and won't boot (it will occasionally mount from linux if i am lucky), so if anyone has pointers i'd be glad to hear them, thanks

---

### Post by frodon on 2008-03-20
Just run an fsck on it, it should fix it (you can use directly dosfsck if you wish).

The partition you want to check must be unmounted and for exmaple if your windows partition is /dev/hda1 the command to use would be :
```
sudo dosfsck -a /dev/hda1
```The -a option tells to correct errors automatically.

What i said is true if it's a FAT32 partition as i'm not sure linux has utilities for NTFS partitions.

Anyway i think if it your windows partition you should be able to repair it with the windows install CD.

---

### Post by submerged2go on 2008-03-20
> **Person98 said:**
> I have been having the same problem i have been using gnome torrent and azerus i am on wireless, the real bad news is i was downloading to my windows harddrive (my linux one is only 8 gigs)  and it crashed so now my windows harddrive is horribly corrupt and won't boot (it will occasionally mount from linux if i am lucky), so if anyone has pointers i'd be glad to hear them, thanks

Just to satisfy my curiosity, are you saying that the torrent and downloading was causing the same problems in Windows and Linux itself for your network? I am assuming you are implying it is on both, however it was not quite clear to me. 

I was going to comment that it would have been rather unusual for Windows (I'm assuming you're using Win XP here) to have crashed while downloading as from what I understand, it does not seem to be a common problem for that operating system. Of course, I could be talking a lot of hot air (and I do suspect that I am!:)). 

Frondon is correct about using the Windows CD as that will effectively bring the system back to default, either through System Restore or a re-installation. Alternatively if you do not use Windows as much, you could always just go totally Ubuntu?

---

### Post by frodon on 2008-03-20
Here the issue is with linux WIFI drivers, i can reproduce this with various apps using lot of bandwidth.

---

### Post by submerged2go on 2008-03-21
> **frodon said:**
> Here the issue is with linux WIFI drivers, i can reproduce this with various apps using lot of bandwidth.

Ah, so it is. Well, the latest Hardy kernel I am currently using allows a lot of bandwidth to be used without any faults whatsoever....from what I can see. Only problem with Xubuntu is that there's no quick and easy way for me to see the error logs in kern, sys and messages. Quite a departure from Gnome...

---

### Post by Person98 on 2008-03-21
> **submerged2go said:**
> Just to satisfy my curiosity, are you saying that the torrent and downloading was causing the same problems in Windows and Linux itself for your network? I am assuming you are implying it is on both, however it was not quite clear to me. 

I was going to comment that it would have been rather unusual for Windows (I'm assuming you're using Win XP here) to have crashed while downloading as from what I understand, it does not seem to be a common problem for that operating system. Of course, I could be talking a lot of hot air (and I do suspect that I am!:)). 

Frondon is correct about using the Windows CD as that will effectively bring the system back to default, either through System Restore or a re-installation. Alternatively if you do not use Windows as much, you could always just go totally Ubuntu?

I tried torrenting with windows and it froze but that was after i think  the harddrive was corrupted, it got progressively worse, and i need windows for a 3d cad programs for school (ie not alternative and i can't get it running with wine) i think i am going to have to go for the reinstallation thanks for your help.

---

### Post by AstarothCY on 2008-03-22
Hey everyone, I should say that I am now having similar problems in WinXP, and I am certain that the problem is my wifi USB dongle (Zyxel G-260). It will freeze my computer completely, but the difference with Linux is in WinXP I can just disconnect the dongle and the computer will just wake up and work normally without rebooting. Also, when it crashes, the LED of the dongle turns off, and sometimes the LED will flash and will cause my PC to slow down during the flashing.

I've contacted Zyxel support for this but I suspect we may be experiencing a few distinct problems here.

---

### Post by jward3010 on 2008-05-04
This post is definitley in the realm of the problem I am having but I'm very much along submerged2go's side of this.

The first ubuntu I installed was 7.10 Gutsy and I got Azureus for torrents and had kernel panic problems after any amount of time (could be 30 mins. or 6 hours) so very similar problems. I have recently done a fresh install of 8.04 Hardy and now I use Transmission and I was shocked to find the native torrent client also having the same kernel panic problems. I started the PC at 4:15AM (don't ask me why so late, I was coming back from a party) and put a tomboy note on display beside Transmission saying "PC stable at 4:15" and when I came down the next morning the PC had crashed and had a kernel panic (Caps and Scroll Lock flashing on keyboard)and on-screen I noted the time up in the top right corner and it was 4:35 (which is the time of the crash as it had froze the time on the display) so I got 20 minutes of downloading and uploading through Transmission.

I want to point out that I use a wired connection (an onboard Marvell 88E8001 Gigabit NIC running at 100Mbps on a 100Mbps LAN) and to put it bluntly I have to use Windows for torrents as it doesn't have any problems with Azureus and crashing with torrents. My torrents are downloaded to a seperate 250GB NTFS drive (SATA II). I don't think this problem is purely network based. One thing to do would be to leave System Monitor running on screen while Transmission / Azureus runs and see if the memory leak problems are true. Basically whenever the crash happens maybe at that stage the SWAP file will show up as full as well as memory?

What I'll try is downloading Azureus on 8.04 and see if it using things differently from Transmission (maybe Azureus is stable with 8.04). I also have an Nvidia Gigabit controller on my board whcih I could try using instead of the Marvell and I'll report back on these things.

To finish here's my system specification:
AMD Athlon 64 3700 (overclocked from 2.2GHz to 2.53GHz)
1GB Corsair XMS4400 PC4400 (550MHz) RAM (2 X 512MB matched)
Asus A8N-Deluxe motherboard with nForce4 chipset
nVidia 7800GTX graphics card (proprietary drivers installed)
250GB DiamondMax10 S-ATA II HD
250GB Samsung Spinpoint S-ATA II HD
Plextor PX-716A DVD-RW / DL drive
LG DVD-RW / DL 16X drive
Sony 3.5" Floppy Drive
Creative Audigy 2ZS Sound

---

### Post by frodon on 2008-05-04
No sure you followed this thread, the problem has already been located and it is the wireless driver.
If you use wired connection then this is not the right thread, hardy has shown to produce hard lockups on some configuration and this is independent of the apps you are running.

---

### Post by jward3010 on 2008-05-04
Well I followed the thread right through (read the whole thing) and did read all the ones about wireless card driver problems but there was still some discussion that didn't relate to wireless cards such as submerged2go's posts which were about the fact he had a wired connection and still was having the same problem, and hence I thought this is an appropriate place to post my problems which are absolutely identical.

You could just be right about spontaneous lock-ups in Hardy because I have run Transmission from 2:30PM today until now which is 9:15PM and no problems so maybe everything is alright and that kernel panic yesterday was just coincidental, although I'm not completely convinced as I had horrible problems (as I have said in my main post) with Azureus under 7.10 Gutsy and kernel panics.

Out of interest is there a specific thread for torrent lock-ups and wired connections that I should be posting in because I'll do that if there is.

Thanks, JOHN.

---

### Post by jward3010 on 2008-05-05
I'm glad to say that I ran Transmission all through last night and no crashes or freezing or kernel panics so it probably is sorted in Hardy, and because I prefer Azureus I'll move to it today and see how I get on with it.

Thanks.

---

