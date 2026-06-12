---
title: "Winfast motherboard and SIS integrated graphic card freezing."
date: 2013-04-03
forum: General Help
---

### Post by JanezMurn1988 on 2013-04-03
Hello,

I wanted to install an old ubuntu on my old machine. (Winfast motherboard, SIS integrated graphic card, 512MB RAM, AMD processor...). First I've tried to
install the newest but there was no picture on the beginning screen. Ubuntu 8.04 did good but it's freezing very offten (every 5 minutes). I didn't find anything
interesting in the log files. I've also tried with Lubuntu, Xubuntu and Mint (64 and 32 bit). Same problem in all distributions... SIS drivers are installed... Maybe there is 
a bug in there? If anyone can give me some smart advice I would be really pleased.

Thank you, Janez

---

### Post by mörgæs on 2013-04-03
Hi, welcome to the fora.

SIS has never been famous for supporting Linux, so it might be a struggle.

Have you tried installing only with open-source drivers? 
Have you checked the memory by running **memtest** from the boot menu? Best is to let it run for at least an hour.

---

### Post by JanezMurn1988 on 2013-04-03
Hello,

It was also happening with live CD... I've tried with open source drivers only... No luck :(. I hoped that there is already a solution for this problem, but didn't find anything handy on google.
It is working super fast but suddenly it freezes and need a reboot. I don't think that a problem is in RAM. Because I have 2 alike computers and it's happening on both. Only difference
is that one has 512 MB of ram and the other one has 1024 (2 slots). What else can I do? :( Do you think that Fedora or any other distro should work? If the problem is in the kernel then
I can't do anything or can I?

Best regards, Janez

---

### Post by mörgæs on 2013-04-03
I still think you should try memtest.

Also, if the computer has a steady moment please run **sudo lshw > lshw.txt** and post lshw.txt.

---

### Post by JanezMurn1988 on 2013-04-04
```
testni-desktop
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 760GXK8MC
       vendor: WinFast
       physical id: 0
       serial: WYWM54809359
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (10/08/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket 940
          size: 1800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32 module=amd64_agp
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: ATA Disk
                product: ExcelStor Techno
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PF2O
                serial: PFD210K2E06LKB
                size: 76GiB (82GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009303e
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 7f1d671a-7bf7-4585-bfd7-9d94ee4b3e08
                   size: 75GiB
                   capacity: 75GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2013-03-25 15:39:46 filesystem=ext3 modified=2013-04-02 07:46:16 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-04-02 07:41:45 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1278MiB
                   capacity: 1278MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1278MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DW-552GA
                vendor: TEAC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: R4K4
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:01:6c:fd:92:57
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=10.13.10.125 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_sis latency=32 module=sata_sis
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
```

---

### Post by claracc on 2013-04-04
I have lubuntu 12.04 installed in an old pentium III, CPU 1GHz, 512 MB ram, 20 GB HDD, sis 630/730 graphics card with 64 MB and it works well, you can try the alternate CD installation. I recommend you to try lubuntu 12.04, not 12.10 since there is a bug with certain graphics driver: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1077975](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1077975)

---

### Post by JanezMurn1988 on 2013-04-04
I've tried with ubuntu, lubuntu, xubuntu 12.04 with no luck... I didn't even manage to come into the OS with live CD's... Graphic card problem probably :(... So 12.04 versions don't even show the desktop.. older versions are freezing... Maybe there is already a solution and I didn't find it...

---

### Post by JanezMurn1988 on 2013-04-04
Memtest didn't find any errors.. It was working for like 2 hours. Hm... That's really weird... The computer is working perfectly and then suddenly freezes... Most of the time when I run open office or update manager. But with other applications as well but not that offten... Any other suggestions? Is anything weird in lshw writeout?

---

### Post by mörgæs on 2013-04-04
Only that you are using ext3 :-)

No, seriously I don't see anything strange except the SIS card, as I mentioned above. If you have another graphics card you could try to swap them. 

Have you tried [catching the log files]("https://help.ubuntu.com/community/DebuggingSystemCrash")?

---

### Post by kurt18947 on 2013-04-04
I've been trying different distros on a 2001 Vintage PIII/512 mb. RAM.  If you can download them easily, you might try PCLinuxOS or maybe Salix.  Salix MATE is perhaps the fastest but it's nowhere near *buntu in usability.  PCLinuxOS has a few different Desktops. LXDE seems to work pretty well.  For reasons I was unable to determine, Lubuntu would not install; the installer would hang. Xubuntu would install and run but not as fast as Salex w/ MATE.

---

### Post by mörgæs on 2013-04-04
Well, what do you know. I happened to have a Fujitsu Siemens around with the same graphics card:

```
scenic
    description: Mini Tower Computer
    version: SCEP2
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=mini-tower uuid=0CA42ECC-23B1-11DA-AD7A-003005B06E9C
  *-core
       description: Motherboard
       product: D2140
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: S26361-D2140
       serial: B00B6F26
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS // Phoenix Technologies Ltd.
          physical id: 0
          version: 5.00 R1.10.2140.01
          date: 07/13/2005
          size: 118KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: CPU
          size: 2800MHz
          capacity: 2800MHz
          width: 64 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 20KiB
             capabilities: burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             physical id: 0
             slot: DIMM-1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2,5 ns)
             physical id: 1
             slot: DIMM-2
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64
          resources: irq:0 memory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:2000(size=4096) memory:fc100000-fc1fffff memory:f0000000-f7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:f0000000-f7ffffff memory:fc100000-fc11ffff ioport:2000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c00(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD400BB-55JK
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAMF1946861
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000a958c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 788ed97a-95ba-495d-8dac-b6e55fe69a12
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-09-17 20:30:54 filesystem=ext4 lastmountpoint=/ modified=2012-09-17 21:10:10 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2013-02-03 11:03:51 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 990MiB
                   capacity: 990MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 990MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Maxtor 4D040H2
                vendor: Maxtor
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: DAH0
                serial: D23J8L8E
                size: 38GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c97bd
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 0fcb2bc9-3cf9-4535-99b4-d676922121cf
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-11-14 17:12:19 filesystem=ext4 modified=2012-11-14 19:49:37 mounted=2012-11-14 19:16:21 state=clean
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GDR8163B
                vendor: HL-DT-ST
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/sr0
                version: 0F21
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD writer
                product: DVDRW SHW-160P6S
                vendor: LITE-ON
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr1
                version: PS09
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=173 maxlatency=11 mingnt=52
             resources: irq:18 ioport:1400(size=256) ioport:1000(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:fc000000-fc000fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:fc001000-fc001fff
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:fc002000-fc002fff
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:fc003000-fc003fff
        *-network
             description: Ethernet interface
             product: NC100 Network Everywhere Fast Ethernet 10/100
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.21 latency=64 maxlatency=128 mingnt=64 multicast=yes
             resources: irq:19 ioport:1800(size=256) memory:fc004000-fc0043ff memory:40000000-4001ffff
  *-power UNCLAIMED
       description: S26113-E472-V60
       physical id: 1
       version: GS01 REV06
       serial: 169948
       capacity: 180mWh


```

Everything is working fine with a standard Lubuntu 12.04. No need for swapping graphics cards.

---

### Post by JanezMurn1988 on 2013-04-05
That's really weird. I can't even start the Lubuntu 12.04 installer... Do you have any idea why? When I click  install or try it it's loading with low colors and then there is a black screen. Same is with ubuntu and xubuntu.

---

### Post by mörgæs on 2013-04-05
The alternate ISO as mentioned by claracc should always be the first one tries if the standard ISO fails. 

Have you tried a server install for comparison?

---

### Post by sebabollatti on 2014-03-26
Hi!
Got the same problem with Winfast 760GXK8MC, Sempron 2800 with 1 Gb of RAM even with a GeForce 6800 at AGP slot... I installed Lubuntu 13.10 32 bits with alternate cd, struggle a bit with graphics resolution and so and suddently goes blank after use it for a while and even shutdown button doesnt do anything... have to unplug power cable

---

### Post by mörgæs on 2014-03-26
There are workarounds for 13.10, but the easiest solution is probably something 12.04-based like [Bodhi Linux]("http://www.bodhilinux.com/").

---

