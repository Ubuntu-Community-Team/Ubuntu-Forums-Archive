---
title: "&quot;could not write bytes: broken pipe&quot; over and over again"
date: 2013-09-16
forum: General Help
---

### Post by Srdjan_Gavrilovic on 2013-09-16
Hi there,
I migrated to new laptop ~10 days ago and since that time  my nightmare doesnt stop. My system keeps crashing over and over. Every  time it is the same. When I start the laptop, it tries to boot, purple  Ubuntu screen flashes and gets black only showing
[highlight]could not write bytes: broken pipe[/highlight]

I  know that this issue is raised already few times and I went through  many of them and nothing worked. I already reinstalled system 3-4 times  and every time it gets to the same thing. Ubuntu runs fine for 1-3 days and  it crashes in a way thet looks to me as the same.

Could you, PLEASE, help me to figure it out?


Hereunder  I listed what you can find at the end of the post. Its just to make  things more compact and then you can look for what you need at the end
my hardware
```
sudo lshw
```

my OS (at the moment I run it al liveCD but thats the one installed and this is the CD I installed it from)
```
lsb_release -a
```

my partitions
```
sudo fdisk -l
```

I tried to update and upgrade while running live CD
```

sudo mount /dev/sda1 /mnt
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
dpkg --configure -a
apt-get update
apt-get upgrade
dpkg --configure -a

```

reboot after failed as well :(

While installing I had a problem wit Broadcom STA wireless driver so I hamered it in a bit
```

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter
cat /etc/modprobe.d/* | egrep 'bcm'
cd /etc/modprobe.d/
sudo gedit blacklist.conf

```
And I put a # in front of the line: blacklist bcm43xx

So I thought It might be a problem with non propitiatory drivers so I tried this
[http://ubuntuforums.org/showthread.php?t=2058521](http://ubuntuforums.org/showthread.php?t=2058521)

nothing positive to report here :(

.
.
.

I tried 10-15 different things I could found online and non of them worked. I'm out of ides

Best, Srdjan


My laptop
```
sudo lshw
ubuntu                    
    description: Laptop
    product: Latitude E5530 non-vPro (Latitude E5530 non-vPro)
    vendor: Winbond Electronics
    version: 01
    serial: 7PS5NX1
    width: 64 bits
    capabilities: vsyscall32
    configuration: boot=normal chassis=laptop sku=Latitude E5530 non-vPro uuid=44454C4C-5000-1053-8035-B7C04F4E5831
  *-core
       description: Motherboard
       product: 05GRXT
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: /7PS5NX1/CN1296137V02E9/
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A11
          date: 05/20/2013
          size: 64KiB
          capacity: 13MiB
           capabilities: pci pnp upgrade shadowing cdboot bootselect  socketedrom edd int13floppy1200 int13floppy720 int13floppy2880  int5printscreen int9keyboard int14serial int17printer acpi usb  smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-3130M CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 53
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-3130M CPU @ 2.60GHz
          slot: SOCKET 0
          size: 1200MHz
          capacity: 2600MHz
          width: 64 bits
          clock: 100MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr  pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx  fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon  pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni  pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid  sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx f16c lahf_lm  arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid  fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L2 cache
             physical id: 43
             slot: CPU Internal L2
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:1
             description: L1 cache
             physical id: 44
             slot: CPU Internal L1
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 45
             slot: CPU Internal L3
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 46
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: NT4GC64C88B1NS-DI
             vendor: Nanya Technology
             physical id: 0
             serial: 01760905
             slot: Top Slot
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: Bottom Slot
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Ivy Bridge Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:f6400000-f67fffff memory:e0000000-efffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: Panther Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:40 memory:f7f00000-f7f0ffff
        *-communication
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:f7f1b000-f7f1b00f
        *-usb:1
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7f18000-f7f183ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f7f10000-f7f13fff
        *-pci:0
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f7e00000-f7efffff
           *-network
                description: Network controller
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=bcma-pci-bridge latency=0
                resources: irq:17 memory:f7e00000-f7e03fff
        *-pci:2
             description: PCI bridge
             product: Panther Point PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:f7200000-f7bfffff ioport:f0a00000(size=10485760)
        *-pci:3
             description: PCI bridge
             product: Panther Point PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:d000(size=4096) memory:f6800000-f71fffff ioport:f0000000(size=10485760)
        *-pci:4
             description: PCI bridge
             product: Panther Point PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f7d00000-f7dfffff
           *-generic
                description: SD Host controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:f7d00000-f7d001ff
        *-pci:5
             description: PCI bridge
             product: Panther Point PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:f7c00000-f7cfffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5761 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth0
                version: 10
                serial: f0:1f:af:30:03:42
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm vpd msi pciexpress bus_master cap_list  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
                configuration: autonegotiation=on  broadcast=yes driver=tg3 driverversion=3.128 firmware=5761-v3.80  latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:f7c10000-f7c1ffff memory:f7c00000-f7c0ffff
        *-usb:2
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:f7f17000-f7f173ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
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
             product: Panther Point 6 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
              resources: irq:42 ioport:f0b0(size=8) ioport:f0a0(size=4)  ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32)  memory:f7f16000-f7f167ff
        *-serial UNCLAIMED
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7f15000-f7f150ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS725050A7
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: GH2O
             serial: TF755AXEJPE26D
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000c433b
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/f3fcebcc-cff9-4e68-8a70-b41426c1f265
                version: 1.0
                serial: f3fcebcc-cff9-4e68-8a70-b41426c1f265
                size: 68GiB
                capacity: 68GiB
                 capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink extents ext4 ext2  initialized
                configuration: created=2013-09-07  15:07:15 filesystem=ext4 lastmountpoint=/ modified=2013-09-16 20:06:48  mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered  mounted=2013-09-16 20:25:24 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3980MiB
                capacity: 3980MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3980MiB
                   capabilities: nofs
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /media/MIX
                version: 1.0
                serial: c829c94f-a60a-42d5-89da-0b6baba528ba
                size: 325GiB
                capacity: 325GiB
                 capabilities: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2013-09-07 17:17:19  filesystem=ext4 label=MIX lastmountpoint=/media/sda3 modified=2013-09-16  20:29:58 mount.fstype=ext4  mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2013-09-16  20:29:58 state=mounted
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                logical name: /media/WORK
                version: 1.0
                serial: 6ca4b4b3-8a62-440b-8160-a54f923e0c6a
                size: 67GiB
                capacity: 67GiB
                 capabilities: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2013-09-07 17:17:26  filesystem=ext4 label=WORK lastmountpoint=/media/sda4  modified=2013-09-16 20:29:47 mount.fstype=ext4  mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2013-09-16  20:29:47 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW SN-208DN
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /cdrom
             version: D100
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=0734a21a state=mounted
              *-volume UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 2
                   version: FAT12
                   serial: 6376-a03b
                   size: 15EiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
  *-battery
       product: DELL HMYXT36
       vendor: LG
       physical id: 1
       version: 06/04/2013
       serial: 3F53
       slot: Sys. Battery Bay
       capacity: 62160mWh
       configuration: voltage=11.1V
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 65mWh
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 0c:84:dc:8e:7a:fa
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=brcmsmac  driverversion=3.8.0-29-generic firmware=N/A ip=192.168.0.100 link=yes  multicast=yes wireless=IEEE 802.11bgn

```

My OS
[highlight]lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
[/highlight]

my partitions
[highlight]sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c433b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   143362047    71680000   83  Linux
/dev/sda2       968620030   976771071     4075521    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3       143362048   826675199   341656576   83  Linux
/dev/sda4       826675200   968617983    70971392   83  Linux
/dev/sda5       968620032   976771071     4075520   82  Linux swap / Solaris

Partition table entries are not in disk order
[/highlight]

---

### Post by sanderj on 2013-09-17
I would select memtest86+ from the GRUB boot menu, and keep that running for a few hours to see if there are any memory related problems.

---

### Post by Srdjan_Gavrilovic on 2013-09-17
> **sanderj said:**
> I would select memtest86+ from the GRUB boot menu, and keep that running for a few hours to see if there are any memory related problems.

I already run diagnostics, TWICE, to make sure.
on boot F12, option "Diagnostics" under "OTHER OPTIONS:"
It took around 1.5-2h and everything came out to be fine. No problems. At least, not reported.

---

### Post by Mephisto Pheles on 2013-09-17
> could not write bytes: broken pipe
is an error I keep getting on and off, it disappears again and comes back some time later. But my system runs fine regardless of the error, so I doubt this is what's crashing your laptop.

A black screen usually indicates driver problems. You have installed all proprietary drivers you might need?

---

### Post by VMC on 2013-09-17
That link you provided is for nvidia, and you have intel.
What does this mean "[COLOR=#000000]I migrated to new laptop ~10 days ago and since that time my nightmare doesnt stop." [/COLOR]Was Ubuntu running on another system and you just use that hard drive on your new system?

Have you tried adding *nomodeset* to the boot string?

---

### Post by Srdjan_Gavrilovic on 2013-09-17
Mephisto Pheles, that is exactly my problem that I have no idea what is a  reason for these repetitive crashes. I believe that all of my drivers  were/are installed.

> **VMC said:**
> That link you provided is for nvidia, and you have intel.
What does this mean "[COLOR=#000000]I migrated to new laptop ~10 days ago and since that time my nightmare doesnt stop." [/COLOR]Was Ubuntu running on another system and you just use that hard drive on your new system?

Have you tried adding *nomodeset* to the boot string?

Me migrating to new lap top means that a  hinge on my old 32bit laptop broke and I bought new 64bit DELL laptop  with Ubuntu 12.04 on it. It crashed and I tried to reinstall it by  myself. I did it already with few other comps and I don't think it is a  big deal. All other comps are doing fine.
It is already matter of  my desperate intention to start things going. I tried everything I  could find. At the end I tried everything people talked about no mater  if I understand them or not. I'm user with very limited understanding of  software. Its just that I never had any bigger problem.

I did not try *nomodeset. *I  gave up on this thing (I reinstalled it way to many times) and I went for 13.04 just to see if its going to  make difference. For now it works fine. Wish me luck for my system not  to crash over next few days :)

Best, Srdjan

---

