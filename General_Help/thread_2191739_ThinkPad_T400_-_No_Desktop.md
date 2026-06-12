---
title: "ThinkPad T400 - No Desktop"
date: 2013-12-04
forum: General Help
---

### Post by amjjawad on 2013-12-04
Hi,

I have installed Xubuntu 13.10 amd64 on ThinkPad T400 for my neighbour and converted his laptop from Windows to Linux.

It was about 24hours later, he told me that he can't login to his desktop anymore. He got the Splash Screen where there is Xubuntu Logo and the circle spinning and that is all. I tried with him some steps but we both agreed that he come over to drop his laptop so I can have a better look.

I am not sure what exactly he has done but he said he tried to install dropbox and iTunes and it seems he managed to install dropbox but of course couldn't install iTunes from their website.

Anyway, any idea what should be done?

Thanks!

---

### Post by fantab on 2013-12-04
More info about the Laptop specs would help.
Does this laptop have '[Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")'? If it does, then I would start diagnosing this aspect. It may be possible that your friend may have been prompted for 'additional driver' and must have accepted it. 
More info:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Also remove 'quite splash' from kernel line and check what's going on.

---

### Post by amjjawad on 2013-12-04
Hi,

> **fantab said:**
> More info about the Laptop specs would help.

Hope this help:

Thinkpad T400 with Centrino 2 @2.53GHz with 3GB RAM - Intel  Graphics - Wireless driver = iwlwifi.

I can't get more information at the moment from that laptop because my neighbour forgot to bring the charger and the laptop is off now but this information I had previously. The charger should be here in less than an hour!

>  Does this laptop have '[Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")'? If it does, then I would start diagnosing this aspect. 
I am not sure. How to check? 

```
lshw -C display 
```

correct?

> It may be possible that your friend may have been prompted for 'additional driver' and must have accepted it. 
I don't think so. The laptop was working fine and Intel does not need 'additional drivers' AFAIK. And, I have asked him about what he did so he didn't mention anything about the drivers! 

> More info:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I will have a look, thanks :)

> Also remove 'quite splash' from kernel line and check what's going on.
I might try this as well :)

By the way, I can enter the recovery mode easily!

---

### Post by amjjawad on 2013-12-06
I can enter the recovery mode but still no desktop (GUI)!

---

### Post by amjjawad on 2013-12-06
```
quite splash
```
Has been removed, nothing happened. 

It drops to tty1

After logging in (CLI), typing:
```
startx
```
Gives black screen and nothing happened

NOT sure what to do next?

---

### Post by amjjawad on 2013-12-06
```
xubuntu
    description: Notebook
    product: 276594U ()
    vendor: LENOVO
    version: ThinkPad T400
    serial: R821N5X
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=ThinkPad T400 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=3B28C081-4FC1-11CB-B638-E9B0ADC99989
  *-core
       description: Motherboard
       product: 276594U
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: VQ1AT03C1NF
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7VET84WW (3.14 )
          date: 04/19/2010
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
          slot: None
          size: 2534MHz
          capacity: 2534MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: burst internal write-back unified
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: M471B5673FH0-CF8
             vendor: Samsung
             physical id: 0
             serial: 989FF606
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: M471B2874EH1-CF8
             vendor: Samsung
             physical id: 1
             serial: 95B0C5B2
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:bff00000-bfffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV620 [Mobility Radeon HD 3400 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:47 memory:c0000000-cfffffff ioport:2000(size=256) memory:bfff0000-bfffffff memory:bff00000-bff1ffff
        *-display
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:fc000000-fc3fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-communication
             description: Communication controller
             product: Mobile 4 Series Chipset MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:49 memory:fc625800-fc62580f
        *-network
             description: Ethernet interface
             product: 82567LF Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:27:13:66:14:bd
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:46 memory:fc600000-fc61ffff memory:fc624000-fc624fff ioport:1820(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1840(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1860(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:1880(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fc625c00-fc625fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:51 memory:fc620000-fc623fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:a000(size=4096) memory:a0200000-a03fffff ioport:a0400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:9000(size=4096) memory:f4200000-f42fffff ioport:a0000000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:26:c6:bd:45:e8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-52-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:50 memory:f4200000-f4201fff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=4096) memory:f8000000-f9ffffff ioport:f4000000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:4000(size=4096) memory:fa000000-fbffffff ioport:f4100000(size=1048576)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18e0(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:fc626000-fc6263ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=16384) memory:f4300000-f7ffffff ioport:f0000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:15:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b01716150-b0171614f irq:16 memory:f4300000-f4300fff ioport:5400(size=256) ioport:5000(size=256) memory:f0000000-f3ffffff memory:a4000000-a7ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:15:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:f4301000-f43017ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:1c00(size=32) memory:fc625000-fc6257ff
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2320B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0084
                serial: K84DTA125BUG
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ea605
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/b55bd391-21c4-4e2d-a7df-4faf095afc09
                   version: 1.0
                   serial: b55bd391-21c4-4e2d-a7df-4faf095afc09
                   size: 49GiB
                   capacity: 49GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2013-11-21 01:16:04 filesystem=ext4 lastmountpoint=/ modified=2013-12-06 22:14:08 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,user_xattr,barrier=1,data=ordered mounted=2013-12-06 22:14:08 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/0b26dba6-bec9-4bed-bf55-25bb5af21b22
                   version: 1.0
                   serial: 0b26dba6-bec9-4bed-bf55-25bb5af21b22
                   size: 245GiB
                   capacity: 245GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2013-11-21 01:16:07 filesystem=ext4 lastmountpoint=/home modified=2013-12-06 22:20:26 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,user_xattr,barrier=1,data=ordered mounted=2013-12-06 22:20:26 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 818de783-27eb-408d-a935-9cd61c547e53
                   size: 3074MiB
                   capacity: 3074MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7930H
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.D0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fc626400-fc6264ff ioport:1c20(size=32)
     *-scsi
          physical id: 1
          bus info: usb@2:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 3819MiB (4004MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000d9e28
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT32
                serial: 6e89-1dd2
                size: 3817MiB
                capacity: 3818MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
  *-battery
       product: 42T4644
       vendor: SANYO
       physical id: 1
       slot: Rear
       capacity: 84240mWh
       configuration: voltage=10.8V


```

---

### Post by fantab on 2013-12-06
>  *-display
                description: VGA compatible controller
                [COLOR=#8b4513]product: RV620 [Mobility Radeon HD 3400 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)[/COLOR]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:47 memory:c0000000-cfffffff ioport:2000(size=256) memory:bfff0000-bfffffff memory:bff00000-bff1ffff
        *-display
             description: Display controller
             [COLOR=#8b4513]product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation[/COLOR]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:fc000000-fc3fffff memory:d0000000-dfffffff ioport:1800(size=8)

So you do have 'Hybrid Graphics'.
More info:
[https://wiki.archlinux.org/index.php/Hybrid_graphics](https://wiki.archlinux.org/index.php/Hybrid_graphics)

---

### Post by amjjawad on 2013-12-07
Because I have no time and because I felt there is more problems with this  installation, not only the graphics issue, I have removed 13.10 and  installed Xubuntu 12.04.3 and I just can NOT believe how fast the laptop  became??!! I think Xubuntu 12.04 is faster than 13.10 and so far,  ThinkPad T400 has no issue at all. Did not even ask for additional  drivers. Everything is great now except iTunes and that is being  discussed on different thread on the mailing list.

Maybe Xubuntu 13.10 with Kernel 3.11 series will not work as good as Xubuntu 12.04 with Kernel 3.2 series :)

Thank you for everything and I will keep an eye on the laptop for 24 hours to see if there will be any issue and report back :)

---

### Post by amjjawad on 2013-12-09
Marked as Solved.
For now, the machine is up and running with Xubuntu 12.04.3 and became even faster (Xubuntu 12.04.3 seems better and faster than 13.10).

Thank you!

---

