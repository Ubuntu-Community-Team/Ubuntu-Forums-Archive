---
title: "CD/DVD drive won't mount"
date: 2013-06-02
forum: General Help
---

### Post by demonic_crow on 2013-06-02
Running Ubuntu 12.04

I can't get my cd/dvd drive to work on my laptop HP DV6700.  It will eject and run when I put a disc in. It just doesn't mount. I do have Windows 7 duel boot and it doesn't even show in the device manager. I have checked the bios and it does have the dvd boot option there so therefor it recognize it. I tried using a LiveCD but it doesn't boot up. I don't believe I have done anything new to cause this problem. I been trying to figure this out for a long time now. I even remove the cd/dvd drive and plug it back in and still have the same issue.

Ouput of **lshw**

```
laptop                    
    description: Notebook
    product: ()
    vendor: Hewlett-Packard
    version: Rev 1
    serial: None
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=oem-specific chassis=notebook family=103C_5335KV
  *-core
       description: Motherboard
       product: 30CF
       vendor: Quanta
       physical id: 0
       version: 85.26
       serial: None1
     *-firmware:0
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.30
          date: 04/24/2008
          size: 111KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-60
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: AMD Turion(tm) 64 X2 Mobile TL60
          slot: Socket S1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-firmware:1
          description: BIOS
          vendor: 1
          physical id: 4241
          size: 823KiB
          capacity: 3520KiB
          capabilities: isa mca vesa edd int13floppynec int13floppytoshiba int13floppy720 int14serial int17printer
     *-memory:0
          description: System memory
          physical id: 4
          size: 3703MiB
        *-bank
             description: DIMM DDR2 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP67 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP67 Co-processor
          vendor: NVIDIA Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:f6200000-f627ffff
     *-usb:0
          description: USB controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:18 memory:f6486000-f6486fff
     *-usb:1
          description: USB controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:f6489000-f64890ff
     *-usb:2
          description: USB controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:18 memory:f6487000-f6487fff
     *-usb:3
          description: USB controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:f6489400-f64894ff
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:f6480000-f6483fff
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: memory:f6100000-f61fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 5
             bus info: pci@0000:02:05.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci cap_list
             configuration: driver=firewire_ohci latency=0 maxlatency=4 mingnt=2
             resources: irq:5 memory:f6100000-f61007ff
        *-generic:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:02:05.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=sdhci-pci latency=0
             resources: irq:7 memory:f6100800-f61008ff
        *-generic:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.2
             bus info: pci@0000:02:05.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=r592 latency=0
             resources: irq:7 memory:f6101000-f61010ff
        *-generic:2
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 5.3
             bus info: pci@0000:02:05.3
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=r852 latency=0
             resources: irq:7 memory:f6101400-f61014ff
     *-ide
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:f6484000-f6485fff
        *-disk
             description: ATA Disk
             product: FUJITSU MHZ2250B
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 8909
             serial: K617T852B2T4
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=12f312f2
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: d452525c-7c85-784f-95c2-a8960e7cc5a6
                size: 93GiB
                capacity: 93GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-01-22 01:55:25 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 60e9eade-e8e5-4966-9434-d9c61535292d
                size: 12GiB
                capacity: 12GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-04-03 02:16:35 filesystem=ntfs label=Extra state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 126GiB
                capacity: 126GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 121GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 5314MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 32:6e:65:22:3b:59
          capacity: 100Mbit/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:42 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:4000(size=4096) memory:f2000000-f3ffffff ioport:f0000000(size=33554432)
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 memory:f6000000-f60fffff
        *-network
             description: Wireless interface
             product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: wlan0
             version: 01
             serial: 00:1f:e1:85:6c:e8
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=3.2.0-43-generic firmware=N/A ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:19 memory:f6000000-f600ffff
     *-display
          description: VGA compatible controller
          product: C67 [GeForce 7150M / nForce 630M]
          vendor: NVIDIA Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:16 memory:f5000000-f5ffffff memory:d0000000-dfffffff memory:f4000000-f4ffffff memory:f6280000-f629ffff
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
```

---

### Post by ohnonot on 2013-06-02
has it ever worked on this dual boot installation? does it work in windows?

---

### Post by gordintoronto on 2013-06-03
It sounds like a hardware problem, possibly a cable, possibly the controller.

Try this command: sudo lshw > myconfig.txt

Edit the file with gedit, and search for cdrom, dvd, etc. On my system, it's about 70% of the way through that file.

Is it possible to try the drive on another computer?

---

### Post by demonic_crow on 2013-06-03
> **ohnonot said:**
> has it ever worked on this dual boot installation? does it work in windows?

Has it ever work, yes. Does it now, no. Thats why Im wondering if its a driver issue.

---

### Post by demonic_crow on 2013-06-03
> **gordintoronto said:**
> It sounds like a hardware problem, possibly a cable, possibly the controller.

Try this command: sudo lshw > myconfig.txt

Edit the file with gedit, and search for cdrom, dvd, etc. On my system, it's about 70% of the way through that file.

Is it possible to try the drive on another computer?

I type **sudo lshw > myconfig.txt** in the terminal and it did nothing. I checked my other laptops and the drive wont fit in them.

---

### Post by ohnonot on 2013-06-04
try different media players, iirc some of them can access the drive and play a disk without it having been mounted before.

repeating my question from post #2: does it work in windows???

---

