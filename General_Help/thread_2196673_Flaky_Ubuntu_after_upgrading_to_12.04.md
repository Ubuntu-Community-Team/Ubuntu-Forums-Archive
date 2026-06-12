---
title: "Flaky Ubuntu after upgrading to 12.04"
date: 2013-12-30
forum: General Help
---

### Post by galapogos on 2013-12-30
Hi,

I've recently upgraded my Ubuntu 64bit 10.04 LTS to 12.04, and I've noticed that it's become flakier. It would hang after some period of time, usually when I'm not around, and when I get back, the system is unresponsive and the screen is blank. Also, often when I boot up, after logging in, the desktop screen is empty, with no icons, bars, etc - just a desktop screen.

How can I troubleshoot what's wrong?

---

### Post by claracc on 2013-12-31
More information is needed in order to help:

What are your hardware specifications?, and more specifically what is your graphics card?

You can post here, the results of these commands:

```
sudo lshw
```

```
lspci
```

Meanwhile, you can try some of the workarounds (for the no icons desktop problem) addressed in this thread:
[http://askubuntu.com/questions/164725/my-desktop-disappeared-how-do-i-get-it-back](http://askubuntu.com/questions/164725/my-desktop-disappeared-how-do-i-get-it-back)

---

### Post by galapogos on 2014-01-01
Hi, it's an intel Core i7-3770 on an ASUS P8H77-V with 24GB memory. I was Ubuntu 64bit 10.04 LTS with an upgraded kernel, and was also using a backported intel graphics driver to get dual monitor working correctly. The stock drivers in 10.04 wasn't working well.

Output of sudo lshw:
```

    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=2094D8A4-DAD7-DD11-8210-C86000ECE01C
  *-core
       description: Motherboard
       product: P8H77-V
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: MF70C4G02800271
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0505
          date: 03/16/2012
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal unified
     *-memory:0 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
     *-memory:1
          description: System Memory
          physical id: 60
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-12800CL10-8GBXL
             vendor: Fujitsu
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CMZ32GX3M4X1600C10
             vendor: AMI
             physical id: 1
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-12800CL10-8GBXL
             vendor: Fujitsu
             physical id: 2
             serial: 00000000
             slot: ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-memory:2 UNCLAIMED
          physical id: 2
     *-memory:3 UNCLAIMED
          physical id: 3
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42
        *-display
             description: VGA compatible controller
             product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:44 memory:f7d00000-f7d0ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:46 memory:f7d1a000-f7d1a00f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7d18000-f7d183ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:f7d10000-f7d13fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:df300000-df4fffff ioport:df500000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f7c00000-f7cfffff
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR8161 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 08
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: latency=0
                resources: memory:f7c00000-f7c3ffff ioport:e000(size=128)
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
                resources: iomemory:202001f10-202001f0f
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7d17000-f7d173ff
        *-isa
             description: ISA bridge
             product: H77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi5
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7d16000-f7d167ff
           *-disk:0
                description: ATA Disk
                product: INTEL SSDSC2CT12
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 300i
                serial: CVMP218008A0120BGN
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d2598
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 629bb098-62a9-463b-bfd3-7d1f401474bc
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-07-24 21:34:28 filesystem=ext4 lastmountpoint=/ modified=2013-12-10 09:42:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2014-01-02 09:13:47 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 4693MiB
                   capacity: 4693MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4693MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 05.0
                serial: WD-WCATRC228955
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=65c2c3e4
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/WD-1TB-SATA
                   version: 3.1
                   serial: beb552f9-724d-df44-bd0f-dc5a49e85c9a
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2013-04-10 17:08:30 filesystem=ntfs label=1TB mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-disk:2
                description: ATA Disk
                product: ST380013AS
                vendor: Seagate
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: 3.45
                serial: 4MR16LNS
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cccdcccd
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdc1
                   logical name: /media/80GB
                   version: 3.1
                   serial: 0da05381-7f82-4ef2-8112-fbfcc72c2533
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2013-04-11 17:36:12 filesystem=ntfs label=80GB mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-222BB
                vendor: TSSTcorp
                physical id: 3
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: SB00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7d15000-f7d150ff ioport:f040(size=32)
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.8
       logical name: wlan1
       serial: a0:f3:c1:24:17:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.2.0-030200-generic firmware=1.3 link=no multicast=yes wireless=IEEE 802.11bgn


```

Output of lspci
```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 08)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)

```

compiz error message (StacktraceAddressSignature truncated as it was too long and I was copying it by hand)
```

The application Compiz has closed unexpectedly
ExecutablePath
   /usr/bin/compiz
Package
  unity 5.20.0-0ubuntu2
ProblemType
  Crash
Title
  compiz crashed with SIGSEGV in brw_upload_state()
ApportVersion
  2.0.1-0ubuntu17.6
Architecture
  amd64
CoreDump
CrashCounter
  1
Date
Dependencies
Disassembly
DistroRelease
  Ubuntu 12.04
InstallationMedia
  Ubuntu 10.04 LTS "Lucid Lynx" - Release amd64 (20120214.2)
MarkForUpload
  True
PackageArchitecture
  amd64
ProcCmdline
  compiz-sm-client-id 104e07291f42107fab1388454051735560
ProcEnviron
  LANGUAGE=en SG:zd SG:en
  PATH=(custom, user)
  LANG=en_SG.UTD-8
  SHELL=/bin/bash
ProcMaps
ProcStatus
Registers
SegvAnalysis
  Segfault happened at: 0x7f245d797bdb:   mov 0x218(%rax), %r12
  PC (0x7f245d797bdb) ok
  source "0x218(%rax)" (0x00000218) not located in a known VMA region (needed readable region)!
  destination "%r12" ok
SegvReason
 reading NULL VMA
Signal
  11
SourcePackage
  unity
Stacktrace
StacktraceAddressSignature
  /usr/bin/compiz:11:x86_64:/usr/lib/x86_64-linux-gnu/dri/i965_dri.so+71bdb:/usr/lib/x86_64-linux-gnu/dri/i965_dri.so+67bf0:/usr/lib/x86_64-linux-gnu/dri/i965_dri.so+51788:/usr/lib/x86_64-linux-gnu/dri/i965_dri.so+3e86f:/usr/lib/x86_64-linux-gnu/dri/libdricore.so+10f0d4:/usr/lib/compiz/libopengl.so...
StacktraceTop
Tags
  precise
ThreadStacktrace
Uname
  Linux 3.2.0-030200-generic x86_64
UpgradeStatus
  Upgraded to precise on 2013-11-19 (43 days ago)
UserGroups
  adm admin cdrom dialout lpadmin plugdev sambashare
XsessionErrors

```

---

### Post by Bucky Ball on 2014-01-01
That upgrade can sometimes be problematic, possibly because you are moving from Gnome to Unity desktop environment. You can try reinstalling Unity and also check Software Sources and make sure there are no 10.04 repos still enabled.

Also, run these, one after the other:

```
sudo apt-get update
sudo apt-get upgrade
```

Any error messages?

BTW, the more precise command for graphics details is:

```
sudo lshw -C video
```

;)

---

### Post by galapogos on 2014-01-01
How do I reinstall Unity and check Software Sources?

anyway, lshw - C video gives the following output
```

  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: drivers=i915 latency=0
       resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f0000(size=64)

```

---

### Post by claracc on 2014-01-02
To check software sources, you go to /etc/apt/ directory and there is sources.list file.

Tou can check it to see if there is any reference to 10.04 repositories, you can look at it with the command:

```
less /etc/apt/sources.list
```

---

### Post by Bucky Ball on 2014-01-02
Remove and reinstall Unity:

[http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity)

Software Sources should be available if you type it into the dash, but if not, easiest to open Update Manager>click 'Settings' in the bottom left corner>check the tabs to see if anything relates to 10.04. 

To do in terminal ('less' won't give permission to make any alterations):

```
sudo nano /etc/apt/sources.list
```

Put a hash mark (#) before anything that relates to 10.04.

---

### Post by galapogos on 2014-01-02
Thanks. I've checked sources.list and everything seems to be precise, the lucid entries are all commented out.

I've also updated the intel drivers via a ppa repository, let's see if things are good over the next few days.

---

