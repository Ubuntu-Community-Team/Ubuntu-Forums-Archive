---
title: "Dell Poweredge 700 Startup Problem"
date: 2013-10-29
forum: General Help
---

### Post by dan.j.allen on 2013-10-29
Hi,

I have a Dell PowerEdge 700 server which was successfully running Ubuntu Server 9.04.  I have attempted to upgrade this to both 12.04 and 13.10 recently.  The installation process is fine for both.  However, when starting the new system, success is intermittent.  Most of the time, the system halts during boot and it appears to be having trouble mounting one of the partitions.  If I re-install 9.04, this does not happen.

Does anybody have any ideas what this could be and if it can be fixed?

Thanks.

---

### Post by mörgæs on 2013-10-29
Welcome to the fora.

Please run 

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags. Can be done in 9.04 if that's the only one available for now.

---

### Post by dan.j.allen on 2013-10-29
Hi and thank you.

It currently has 13.10 installed but luckily did start up first time. lshw.txt posted below:

```

computer
    description: Mini Tower Computer
    product: PowerEdge 700
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0P1158
       vendor: Dell Computer Corporation
       physical id: 0
       version: A00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A06
          date: 01/04/2006
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.3.4
          serial: [REMOVED]
          slot: PROC1
          size: 3400MHz
          capacity: 4GHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             physical id: 0
             slot: DIMM1_A
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             physical id: 1
             slot: DIMM2_A
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             physical id: 2
             slot: DIMM1_B
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             physical id: 3
             slot: DIMM2_B
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-f83fffff
        *-pci:0
             description: PCI bridge
             product: 82875P/E7210 Processor to PCI to CSA Bridge
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:fe300000-fe4fffff
           *-network
                description: Ethernet interface
                product: 82547GI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:01:01.0
                logical name: eth0
                version: 00
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=[REMOVED] latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:18 memory:fe3e0000-fe3fffff ioport:ece0(size=32)
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82875P/E7210 Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-pci:1
             description: PCI bridge
             product: 6300ESB 64-bit PCI-X Bridge
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci pcix normal_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fe100000-fe2fffff ioport:f4000000(size=67108864)
           *-scsi:0
                description: SCSI storage controller
                product: AHA-3960D / AIC-7899A U160/m
                vendor: Adaptec
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: scsi3
                version: 01
                width: 64 bits
                clock: 66MHz
                capabilities: scsi pm bus_master cap_list rom scsi-host
                configuration: driver=aic7xxx latency=32 maxlatency=25 mingnt=40
                resources: irq:24 ioport:dc00(size=256) memory:fe1ff000-fe1fffff memory:fe200000-fe21ffff
           *-scsi:1
                description: SCSI storage controller
                product: AHA-3960D / AIC-7899A U160/m
                vendor: Adaptec
                physical id: 1.1
                bus info: pci@0000:02:01.1
                logical name: scsi4
                version: 01
                width: 64 bits
                clock: 66MHz
                capabilities: scsi pm bus_master cap_list rom scsi-host
                configuration: driver=aic7xxx latency=32 maxlatency=25 mingnt=40
                resources: irq:25 ioport:d800(size=256) memory:fe1fe000-fe1fefff memory:fe100000-fe11ffff
              *-tape
                   description: SCSI Tape
                   product: DAT    DAT72-052
                   vendor: SEAGATE
                   physical id: 0.6.0
                   bus info: scsi@4:0.6.0
                   logical name: /dev/nst0
                   logical name: /dev/st0
                   version: A060
                   serial: [REMOVED]
                   capabilities: removable
                   configuration: ansiversion=3
           *-storage
                description: RAID bus controller
                product: AAC-RAID
                vendor: Adaptec
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: scsi2
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list rom emulated
                configuration: driver=aacraid latency=32 maxlatency=1 mingnt=1
                resources: irq:25 memory:f4000000-f7ffffff memory:fe120000-fe127fff
              *-disk:0
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sda
                   size: 148GiB (159GB)
                   capabilities: partitioned partitioned:dos
                   configuration: sectorsize=512 signature=0001a329
                 *-volume
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      logical name: /dev/sda1
                      logical name: /
                      version: 1.0
                      serial: [REMOVED]
                      size: 148GiB
                      capacity: 148GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2013-10-28 20:33:35 filesystem=ext4 label=Ubuntu Server 13 lastmountpoint=/ modified=2013-10-29 16:14:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-10-29 16:14:31 state=mounted
              *-disk:1
                   description: SCSI Disk
                   physical id: 0.1.0
                   bus info: scsi@2:0.1.0
                   logical name: /dev/sdb
                   size: 372GiB (399GB)
                   capabilities: partitioned partitioned:dos
                   configuration: sectorsize=512 signature=0007eb5a
                 *-volume
                      description: Extended partition
                      physical id: 1
                      bus info: scsi@2:0.1.0,1
                      logical name: /dev/sdb1
                      size: 372GiB
                      capacity: 372GiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/sdb5
                         capacity: 1430MiB
                         capabilities: nofs
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/sdb6
                         logical name: /home
                         capacity: 371GiB
                         configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-disk:2 UNCLAIMED
                   description: SCSI Disk
                   physical id: 1.0.0
                   bus info: scsi@2:1.0.0
              *-disk:3 UNCLAIMED
                   description: SCSI Disk
                   physical id: 1.1.0
                   bus info: scsi@2:1.1.0
              *-disk:4 UNCLAIMED
                   description: SCSI Disk
                   physical id: 1.2.0
                   bus info: scsi@2:1.2.0
        *-usb:0
             description: USB controller
             product: 6300ESB USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bce0(size=32)
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 6300ESB Watchdog Timer
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe500400-fe50040f
        *-generic:2 UNCLAIMED
             description: PIC
             product: 6300ESB I/O Advanced Programmable Interrupt Controller
             vendor: Intel Corporation
             physical id: 1d.5
             bus info: pci@0000:00:1d.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcix io_x_-apic bus_master cap_list
             configuration: latency=0
        *-usb:1
             description: USB controller
             product: 6300ESB USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe500000-fe5003ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:fc000000-fdffffff memory:20000000-200fffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage XL PCI
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: e
                bus info: pci@0000:03:0e.0
                version: 27
                width: 32 bits
                clock: 33MHz
                capabilities: pm vga_controller bus_master vga_palette cap_list
                configuration: latency=32 mingnt=8
                resources: memory:fc000000-fcffffff ioport:cc00(size=256) memory:fdeff000-fdefffff memory:20000000-2001ffff
        *-isa
             description: ISA bridge
             product: 6300ESB LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 6300ESB SATA Storage Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fea0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 6300ESB SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:8c0(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM GDR8163B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 0D20
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc

```

---

### Post by mörgæs on 2013-10-29
Good, if it works now then please mark the thread solved using 'thread tools'. You can always remove the flag and post again if the problem should reappear.

---

### Post by dan.j.allen on 2013-10-29
> **mörgæs said:**
> Good, if it works now then please mark the thread solved using 'thread tools'. You can always remove the flag and post again if the problem should reappear.

It doesn't work now. As I stated in my original post, the startup is intermittent, sometimes it starts up successfully but most times it doesn't.  I was lucky it did when you asked for the output file.

I've done some more testing on it as follows:

1. A single drive was installed on the onboard SATA (outside the SATA RAID) and 13.10 installed. This appeared to work fine.
2. The same drive from (1) was installed on the SATA RAID card, and 13.10 installed again. This failed the very first boot.

Therefore, it appears to be the SATA RAID card causing the problem. Is it possible the card in this machine is no longer supported for some reason?

Thanks.

---

### Post by mörgæs on 2013-10-30
Sorry, can't help you more. I have never worked with RAID.

---

