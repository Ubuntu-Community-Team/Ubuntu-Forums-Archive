---
title: "8GB SD card not recognised"
date: 2013-03-23
forum: General Help
---

### Post by Tim036 on 2013-03-23
Its this type of card

8GIG 8GB Memory Card SD SDHC SAMSUNG WB600 WB650 CLASS 10	


It flashes Ok when I plug it in, But cannot see a way of accesing it in Ubunto 12.04

does not show uo in 'File Manager or 'Dolphin'

Have I bought the wrong one ?   In which case what is the right one ?

A very puzzled,

Tim

---

### Post by coldraven on 2013-03-23
It is possible that your card reader cannot read SDHC, try it in a newer device.
See: [http://en.wikipedia.org/wiki/SD_card](http://en.wikipedia.org/wiki/SD_card)

---

### Post by conradin on 2013-03-23
post your result to these commands:

```

#lshw
#lsusb

```

perhaps there is no FS on the device?

---

### Post by Tim036 on 2013-03-23
sudo lshw yielded:- (gulp)
```

 socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X6 1055T Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X6 1055T Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 3300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=6 enabledcores=6
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 768KiB
             capacity: 768KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: pipeline-burst internal varies
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451) Synchronous 667 MHz (1.5 ns)
             product: NT4GC64B8HB0NF-CG
             vendor: Nanya
             physical id: 0
             serial: 643896D2
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451) Synchronous 667 MHz (1.5 ns)
             product: NT4GC64B8HB0NF-CG
             vendor: Nanya
             physical id: 1
             serial: 643852F1
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451) [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-01-28 19:38+0000X-Generator: Launchpad (build 16451) [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fe900000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880 [Radeon HD 4250]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:fe9f0000-fe9fffff memory:fea00000-feafffff
           *-multimedia
                description: Audio device
                product: RS880 HDMI Audio [Radeon HD 4200 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:fe9e8000-fe9ebfff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 03
                serial: 00:30:67:ba:9a:78
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:41 ioport:e800(size=256) memory:fdffb000-fdffbfff memory:fdffc000-fdffffff memory:febe0000-febfffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe8ffc00-fe8fffff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fe000-fe8fefff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fd000-fe8fdfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe8ff800-fe8ff8ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fc000-fe8fcfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fb000-fe8fbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe8ff400-fe8ff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:fe8f4000-fe8f7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fa000-fe8fafff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HDS72103
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: JPFO
             serial: JPB430HN3YDXRD
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00082f55
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 1fea20c3-3a3e-48f0-a2b2-3fbd6b398ece
                size: 290GiB
                capacity: 290GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-03-08 22:15:45 filesystem=ext4 lastmountpoint=/ modified=2013-03-23 12:54:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-03-23 12:55:29 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 7934MiB
                capacity: 7934MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 7934MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
     *-scsi:3
          physical id: 5
          bus info: usb@2:1.1
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdf
             size: 7701MiB (8075MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: W95 FAT32 (LBA) partition
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdf1
                capacity: 7700MiB
                capabilities: primary
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.4
       logical name: wlan1
       serial: 00:1c:df:35:f4:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-26-generic firmware=N/A ip=192.168.1.100 link=yes multicast=yes wireless=IEEE 802.11bg
tim@tim-A880G:~$

```

---

### Post by Tim036 on 2013-03-23
and  lsusb was:-   
```

tim@tim-A880G:~$ sudo lsusb
Bus 001 Device 002: ID 046e:300e Behavior Tech. Computer Corp. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 005 Device 002: ID 04e8:327e Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 5136:4678  
Bus 002 Device 004: ID 050d:705e Belkin Components F5D7050 Wireless G Adapter v5000 [Realtek RTL8187B]
tim@tim-A880G:~$ 

```
_____

modest by comparrison

---

### Post by Tim036 on 2013-03-23
Bus 005 Device 002: ID 04e8:327e Samsung Electronics Co., Ltd 

seems to indicate at least part of the OS knows about it !

I did manage to use Win32Imager to create a Raspbian boot CD on another one of these SD cards and it worked fine when plugged into a RPi !

:  )))

Tim

---

### Post by sandyd on 2013-03-23
Please use code tags (the # button in the editor) when posting code to enable code tags - it makes things a bit cleaner.

Thanks!

---

### Post by Tim036 on 2013-03-23
If I knew what that meant I would.

I just copy and paste what was on my screen.

No editor in sight...  What should I do ?

paste into 'Kate' and trim stuff off it ?

Sorry about not knowing..

:  (

Tim

---

### Post by conradin on 2013-03-23
again, I think your USB stick lacks an FS.
lshw shows /dev/sdf which I suspect is your USB drive.
have your looked for this in the disk utility?
is there any data on the disk?
```

        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdf
             size: 7701MiB (8075MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: W95 FAT32 (LBA) partition
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdf1
                capacity: 7700MiB
                capabilities: primary

```

Thats what I think your usb stick is. 
try mounting it from the command line if the disk utility fails.

---

### Post by sandyd on 2013-03-23
> **Tim036 said:**
> If I knew what that meant I would.

I just copy and paste what was on my screen.

No editor in sight...  What should I do ?

paste into 'Kate' and trim stuff off it ?

Sorry about not knowing..

:  (

Tim
If you paste the stuff, and then select all of it, then click the button in the picture, your code should be in code tags :) - the screenshot shows the post editor
[IMG]https://dl.sandyd.me/public.php?service=files&t=02952ccd5c3b535cc0c490436b627b41&download[/IMG]

---

### Post by Tim036 on 2013-03-24
Wow,  I didn't know that !

With no FS, it looks like I bought the wrong sort of SD card.

Works great for Raspian generation, but not much else.

Anyone got a type that can be seen and can take data files to pass from one PC to another ?

:P:P:P

Tim

---

### Post by Tim036 on 2013-03-24
```
tim@tim-A880G:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      299667048 8449528 275995300   3% /
udev             3917688       4   3917684   1% /dev
tmpfs            1583988    1048   1582940   1% /run
none                5120       0      5120   0% /run/lock
none             3959960     148   3959812   1% /run/shm
tim@tim-A880G:~$ ls

```

Not sure if that helps at all.

:P

Tim

---

### Post by Tim036 on 2013-03-24
Found 'Disk Utility and formatted it with EXT 4 (?) so maybe that will fix it.

:P

Tim

---

### Post by Tim036 on 2013-03-24
Many many thanks for everyone who has responded !

I found 'Disk Utility' and formatting it has fixed it ! It now shows up in Dolphin and accepts data aok !

I have learnt a lot, as I never new Disk Utility existed ! as well as the # key !

This Forum has helped me loads !    

:P:P:P

Tim

---

