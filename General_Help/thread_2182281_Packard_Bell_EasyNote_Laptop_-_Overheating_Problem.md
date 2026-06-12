---
title: "Packard Bell EasyNote Laptop - Overheating Problem"
date: 2013-10-20
forum: General Help
---

### Post by amjjawad on 2013-10-20
Hi,

```
sudo lshw 
packard-bell              
    description: Pizza Box Computer
    product: Packard Bell EasyNote
    vendor: NEC Computers International
    version: PB22C00061
    serial: 610700440237
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=pizzabox power-on_password=disabled uuid=B87434C6-3C97-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: NEC Versa Premium
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 5a
     *-firmware
          description: BIOS
          vendor: Insyde Software Corporation
          physical id: 0
          version: R1.05
          date: 09/20/2005
          size: 84KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology ML-32
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.2
          serial: Processor Serial Number
          slot: uPGA 754
          size: 1600MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: burst pipeline-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst pipeline-burst internal write-back
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          capacity: 768MiB
        *-bank:0
             description: SODIMM DDR 133 MHz (7.5 ns)
             physical id: 0
             slot: DRAM Slot 1
             size: 512MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: SODIMM DDR 133 MHz (7.5 ns)
             physical id: 1
             slot: DRAM Slot 2
             size: 512MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-memory:1 UNCLAIMED
          description: Video Memory
          physical id: d
          slot: System board or motherboard
          capacity: 64MiB
     *-memory:2 UNCLAIMED
          description: Flash Memory
          physical id: e
          slot: System board or motherboard
          capacity: 2MiB
     *-memory:3 UNCLAIMED
          physical id: 1
     *-memory:4 UNCLAIMED
          physical id: 2
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RC4xx/RS4xx PCI Bridge [int gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:c000(size=8192) memory:c0000000-cfffffff ioport:90000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS480M [Mobility Radeon Xpress 200]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:90000000-97ffffff ioport:c000(size=256) memory:c0000000-c000ffff memory:98000000-9801ffff
        *-pcmcia
             description: CardBus bridge
             product: PCI4510 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:17 memory:40000000-40000fff ioport:1800(size=256) ioport:1c00(size=256) memory:44000000-47ffffff memory:48000000-4bffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI4510 IEEE-1394 Controller
             vendor: Texas Instruments
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=128 maxlatency=4 mingnt=2
             resources: irq:18 memory:d0000000-d00007ff memory:d0004000-d0007fff
        *-network:0
             description: Wireless interface
             product: RT2500 Wireless 802.11bg
             vendor: Ralink corp.
             physical id: 15
             bus info: pci@0000:00:15.0
             logical name: wlan0
             version: 01
             serial: 00:10:60:63:4a:2f
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci driverversion=3.11.0-12-generic firmware=N/A latency=128 link=no multicast=yes wireless=IEEE 802.11bg
             resources: irq:18 memory:d0008000-d0009fff
        *-pci:1
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ULi Electronics Inc.
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:a000(size=8192) memory:b8000000-bfffffff memory:88000000-8fffffff
        *-network:1
             description: Ethernet interface
             product: ULi 1689,1573 integrated ethernet.
             vendor: ULi Electronics Inc.
             physical id: 1b
             bus info: pci@0000:00:1b.0
             logical name: eth0
             version: 50
             serial: 00:40:d0:87:8f:60
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 latency=128 link=no maxlatency=40 mingnt=20 multicast=yes port=MII
             resources: irq:20 ioport:e000(size=256) memory:d000a000-d000a0ff
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: ULi Electronics Inc.
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:17 memory:f8002000-f8002fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: ULi Electronics Inc.
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:18 memory:f8003000-f8003fff
        *-usb:2
             description: USB controller
             product: USB 2.0 Controller
             vendor: ULi Electronics Inc.
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=128 maxlatency=32 mingnt=16
             resources: irq:23 memory:40001000-400010ff
        *-multimedia
             description: Multimedia audio controller
             product: M5455 PCI AC-Link Controller Audio Device
             vendor: ULi Electronics Inc.
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=128 mingnt=64
             resources: irq:23 ioport:e100(size=256) memory:d000b000-d000bfff
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ULi Electronics Inc.
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0 mingnt=64
             resources: memory:d000c000-d000cfff ioport:e200(size=256)
        *-isa
             description: ISA bridge
             product: PCI to LPC Controller
             vendor: ULi Electronics Inc.
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0 maxlatency=24 mingnt=1
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ULi Electronics Inc.
             physical id: 1e.1
             bus info: pci@0000:00:1e.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ULi Electronics Inc.
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: c7
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_ali latency=32
             resources: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1100(size=16)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD600UE-22HC
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 09.0
             serial: WD-WXEZ05327384
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000d0945
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 223e8b6f-79c6-4dad-ac54-c4b893f0a093
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-10-18 00:29:02 filesystem=ext4 lastmountpoint=/ modified=2013-10-21 01:51:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-10-21 01:45:21 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /home
                version: 1.0
                serial: 0b507dbf-06cf-4edd-892d-db381fd960b0
                size: 38GiB
                capacity: 38GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-10-18 00:29:07 filesystem=ext4 lastmountpoint=/home modified=2013-10-21 01:51:28 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-10-21 01:51:28 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 518ad65f-ba2b-4e0d-a055-74f26121fad9
                size: 2047MiB
                capacity: 2047MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 5
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD+-RW ND-6650A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.62
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       physical id: 1
       slot: BACK
       configuration: voltage=11.1V
  *-remoteaccess UNCLAIMED
       vendor: Manufacturer Name
       physical id: 2
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:1
       logical name: wlan1
       serial: 00:1f:1f:a8:e5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.11.0-12-generic firmware=0.29 ip=x.x.x.x link=yes multicast=yes wireless=IEEE 802.11bgn


```

This laptop for my neighbour, I have converted her to Linux and breathed new life into her very old machine using Lubuntu 13.10 i386 and I was surprised to noticed the overheating issue even though I have installed Lubuntu which should be light on the hardware.

You need to understand she has been using Windows XP for her entire life and this is not going to make her happy at all.

If you need any more information or a command to run, let me know. Thanks in advance :)

---

### Post by mörgæs on 2013-10-21
I don't know of anything specific for Radeon Xpress 200, but my general approach when dealing with overheating is to disassemble and clean the fan and heat-sink. Surprisingly often it does the trick.

---

### Post by amjjawad on 2013-10-21
> **mörgæs said:**
> I don't know of anything specific for Radeon Xpress 200, but my general approach when dealing with overheating is to disassemble and clean the fan and heat-sink. Surprisingly often it does the trick.

Hi,

But just for the record, this is not the first time I face the same issue with different brand of Laptops even though I clean the fan but that didn't change anything. Is there anything to be done? except cleaning?

---

### Post by mörgæs on 2013-10-22
As I said I don't know of anything specific, but the general steps are cleaning, BIOS upgrade, applying a light system like Lubuntu Core and add Flashblock to the browsers. 

If you still have problems please run **top** for a while to see what is causing the overheating. Does it also happen when the computer is standing idle without anything open?

---

### Post by david98 on 2013-10-22
Is the fan running properly in the past on my last laptop i had the same problem kept overheating cleaned the fan and heatsink but still kept happening so i decided to take a closer look and the fan and the bairings had gone in it. It was not making any unusual sounds that you would think would happen but in the end i replaced the fan problem solved

---

### Post by amjjawad on 2013-12-04
> **david98 said:**
> Is the fan running properly in the past on my last laptop i had the same problem kept overheating cleaned the fan and heatsink but still kept happening so i decided to take a closer look and the fan and the bairings had gone in it. It was not making any unusual sounds that you would think would happen but in the end i replaced the fan problem solved

The fan is working perfectly :)

---

### Post by amjjawad on 2013-12-04
> **mörgæs said:**
> As I said I don't know of anything specific, but the general steps are cleaning, BIOS upgrade, applying a light system like Lubuntu Core and add Flashblock to the browsers.
From experience, cleaning the fan did not solve the case. I still have that on one of my own machines. HP Pavilion DV6 and no matter what I did, the overheating with Linux is even more than Windows.

As for BIOS upgrade, never done that except once and was Windows not Linux. And that one and only time I did was for my laptop that I just told you about above. So, that didn't change anything :)

Yes, Lubuntu is installed. That did not change anything.

Flashblock to the browser? it is overheating without any browser :)

> If you still have problems please run **top** for a while to see what is causing the overheating. Does it also happen when the computer is standing idle without anything open?

'top' didn't show anything unusual and YES, it is HOT even when it is idle. And the fan goes crazy when I do for example:

```
sudo apt-get udpate
```

This happens with me on Packard Bell EasyNote Laptop (that one I started this thread about) and my own machine (HP Pavilion DV6) as well.

That is why I started this thread, because I have tried almost ALL what has been suggested here OR on other threads but that did NOT solve the issue!

Just for the record, I am typing this from Lenovo G570 and I don't have any overheating issue and I can't even hear the fan because it is very silent. So, that makes me think, is it something to do with HP? or Packard Bell?

---

