---
title: "Fujitsu Lifebook NH532: 14.04 LTS freezes randomly"
date: 2015-02-03
forum: General Help
---

### Post by Johan_Alkstl on 2015-02-03
I've recently stared using Ubuntu, installed it on a Fujitsu laptop.

I've been experiencing random freezes, where I can be doing anything and the system will just freeze. I've waited for a long time to see if it was just a really bad lag but it totally freezes. I have to hard reboot to get out of it.

It happens daily and more than once, so any help in solving this would be much appreciated!

---

### Post by Holger_Gehrke on 2015-02-03
Welcome to the forum!

Your post is a bit thin on information. To use a car analogy, it's like telling us the engine in your Ford keeps stalling ...

What model of laptop, what processor, what graphics chip, how much RAM, stock Ubuntu or one of the variants ... ?

The first post in [this thread]("http://ubuntuforums.org/showthread.php?t=1422475") over in the "New to Ubuntu"-Board gives an overview on how to post in such a way as to get helpful responses.

Two suggestions:
1. Can you get to a virtual console when the system freezes ? (ctrl-alt-f1 to f6, you should get a black screen with white text asking you to log in, ctrl-alt-f7 returns to the GUI) If this works, it's "just" the graphics system that's stuck.
2. To reduce damage to the system by hard rebooting, the [Magic SysRq Key combinations]("http://en.wikipedia.org/wiki/Magic_SysRq_key") can be helpful.

---

### Post by Johan_Alkstl on 2015-02-03
Hi Holger and thanks for replying!

Your analogy is correct, because I brought the car to the shop waiting for the mechanics to ask me what they need to know to fix the car. :)

So to answer your questions,

it's a Fujitsu Lifebook NH532, Intel® Core&#8482; i7-3630QM CPU @ 2.40GHz × 8, 8GB RAM, GeForce GT 640M LE/PCIe/SSE2, Stock Ubuntu 14.04 LTS.

There's no other OS on the machine, so it's not dual booted or anything like that. It had Windows 8 originally.

I cannot access any virtual console when it freezes. While I haven't tried any magic SysRq key combo (thanks for that link), I doubt it will react to those either.

Full specs,

description: Notebook
    product: LIFEBOOK NH532 ()
    vendor: FUJITSU
    serial: YLLK002556
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=notebook power-on_password=disabled uuid=D0C96741-2D8E-11E2-80B8-502690184B0C
  *-core
       description: Motherboard
       product: FJNBB2F
       vendor: FUJITSU
       physical id: 0
       serial: 575627-01R2615208
     *-firmware
          description: BIOS
          vendor: FUJITSU // American Megatrends Inc.
          physical id: 0
          version: 2.04
          date: 10/02/2012
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cache:0
          description: L1 cache
          physical id: b
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-through data
     *-cache:1
          description: L2 cache
          physical id: d
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through unified
     *-cache:2
          description: L3 cache
          physical id: e
          slot: L3 Cache
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M471B5273DH0-CK0
             vendor: Samsung
             physical id: 0
             serial: 34820869
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M471B5273DH0-CK0
             vendor: Samsung
             physical id: 1
             serial: 348208B0
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 10
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
          slot: On Board
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
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
             resources: irq:40 ioport:e000(size=4096) memory:f5000000-f60fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GK107M [GeForce GT 640M LE]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:52 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:50 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)
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
             resources: irq:45 memory:f7300000-f730ffff
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
             configuration: driver=mei_me latency=0
             resources: irq:48 memory:f731b000-f731b00f
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
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7318000-f73183ff
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
             resources: irq:51 memory:f7310000-f7313fff
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
             resources: irq:41
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:f7200000-f72fffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 2200
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: c4
                serial: 9c:4e:36:60:d1:28
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-44-generic firmware=18.168.6.1 ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:49 memory:f7200000-f7201fff
        *-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:f6800000-f71fffff ioport:f2100000(size=10485760)
        *-pci:4
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:c000(size=4096) ioport:f2b00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 07
                serial: 50:26:90:18:4b:0c
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:46 ioport:c000(size=256) memory:f2b04000-f2b04fff memory:f2b00000-f2b03fff
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
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7317000-f73173ff
        *-isa
             description: ISA bridge
             product: HM77 Express Chipset LPC Controller
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
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:47 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7316000-f73167ff
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
             resources: memory:f7315000-f73150ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK5076GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: GS00
             serial: X28GC3CXT
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=2484e17e-c02a-4e44-85c8-a26ff7aaabc4 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 8856-c841
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: da11102e-d446-45bd-9d14-17ddb538ddb5
                size: 457GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-01-24 00:25:57 filesystem=ext4 lastmountpoint=/ modified=2015-02-03 10:41:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-02-03 10:41:06 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 12b0339d-8ad4-40b3-afc4-d156a1adbfe6
                size: 8073MiB
                capacity: 8074MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD-MLT UJ260AF
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: CP569291-01
       vendor: FUJITSU
       physical id: 1
       serial: CP5692910101120526120501001449
       slot: Internal Battery
       capacity: 57720mWh
       configuration: voltage=11,1V

---

### Post by Johan_Alkstl on 2015-02-03
I can confirm that Magic SysRq commands do work when the system freezes. So what does that mean?

---

### Post by Holger_Gehrke on 2015-02-03
> **Johan_Alkstl said:**
> I can confirm that Magic SysRq commands do work when the system freezes. So what does that mean?

It means that some emergency measures in the kernel were still working during the freeze. If you did a "sync" and "unmount" before rebooting, you might actually have some interesting entries in your log files.

---

### Post by JeQhdMD on 2015-02-03
Is it correct to assume you've installed the proprietary nvidia drivers?

---

### Post by Johan_Alkstl on 2015-02-04
> **Holger_Gehrke said:**
> It means that some emergency measures in the kernel were still working during the freeze. If you did a "sync" and "unmount" before rebooting, you might actually have some interesting entries in your log files.

Where would I find these log files?

---

### Post by Johan_Alkstl on 2015-02-04
> **JeQhdMD said:**
> Is it correct to assume you've installed the proprietary nvidia drivers?

Yes. I'm using version 331.113 of the proprietary NVIDIA drivers.

---

### Post by Holger_Gehrke on 2015-02-04
> **Johan_Alkstl said:**
> Where would I find these log files?

Log files generally 'live' in '/var/log'. Most of them are simple text files, unless you're using systemd, then a lot of the basic logs are binary and have to be viewed using something called journalctl (or so I believe based on what I've read; not using systemd myself, I'm waiting for it to mature before I decide one way or the other).

---

### Post by Johan_Alkstl on 2015-02-04
What am I looking for? There's a lot of files and folder in /var/log/.

It froze just now and I was able to use RESIUB to restart.

---

