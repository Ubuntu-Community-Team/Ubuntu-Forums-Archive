---
title: "Strange Undeletable Folder"
date: 2013-11-03
forum: General Help
---

### Post by trishtren18 on 2013-11-03
I have a folder sitting within my users home directory that I cannot delete nor view the contents of.  I am not sure what it is or what it does but I am concerned due to the lack of being able to interact with it.  About the only thing I can do is stat it:

# stat Xim7YXHO49/
  File: ‘Xim7YXHO49/’
  Size: 101494784     Blocks: 198248     IO Block: 4096   directory
Device: 802h/2050d    Inode: 9175054     Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2013-11-03 15:44:07.702296961 -0600
Modify: 2013-11-03 15:45:48.898292986 -0600
Change: 2013-11-03 15:45:48.898292986 -0600
 Birth: -

I have not tried to chown it for fear of what it may or may not interact with.  Any help with how to identify this folder and it's content or what to do with it would be much appreciated.

---

### Post by XBNCPRk on 2013-11-03
Isnt XIM a instant messaging broswer extension?

---

### Post by Buntu Bunny on 2013-11-03
There's a Xim mouse and keyboard adapter for Playstation and Xbox.

---

### Post by XBNCPRk on 2013-11-03
Also, the permissions on that folder are 0755 and it belongs to root, so if you elevate your privledges to root from the terminal (using the command sudo -i and then entering the appropriate password when prompted), youll be able to access it so you can at least see what all is in it.

---

### Post by Impavidus on 2013-11-04
To view what's in there you don't even need sudo, as the directory has read and execute permission for all. Just run **ls -al Xim7YXHO49**.
Root-owned directories don't belong in a user's home directory. It may have become root-owned due to misuse of sudo.

---

### Post by pumadeneruda on 2013-12-11
Hi!
I have got the same problem. A few days ago I found a strange folder in my users directory, file type inode, name lW3gIekR 3. Every time I tried to open it my system jammed and had to switch computer off manually. I managed to move it to the trash bin every time I try to delete it or empty the trash my system jams. 
I would appreciate it if some out there could help me. I am very new to Ubuntu, had it installed it on my laptop (a Lenovo G550) just a month ago after many frustrating years as a MS user.
Luigi

---

### Post by gfullmer1 on 2013-12-18
Hi,

I have the same problem.  As of Nov 28th, at least that is what the directory says.  Any ideas?

```
ls -ld OU-qKRRubG/  
drwxrwxrwx 2 gfullmer gfullmer 888315904 Dec 18 16:28 OU-qKRRubG/ (almost a GIG!)


# stat OU-qKRRubG/
  File: ‘OU-qKRRubG/’
  Size: 888315904       Blocks: 1735224    IO Block: 4096   directory
Device: 801h/2049d      Inode: 4202505     Links: 2
Access: (0777/drwxrwxrwx)  Uid: ( 1000/gfullmer)   Gid: ( 1000/gfullmer)
Access: 2013-12-18 16:28:19.785505550 -0700
Modify: 2013-12-18 16:28:15.825505387 -0700
Change: 2013-12-18 16:28:15.825505387 -0700
 Birth: -

My system looks like this:

Linux Dell 3.8.0-22-generic #33-Ubuntu SMP Thu May 16 15:17:59 UTC 2013 i686 i686 i686 GNU/Linux

# lshw
dell                      
    description: Space-saving Computer
    product: Dimension 2400
    vendor: Dell Computer Corporation
    serial: C09JN41
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=space-saving cpus=1 power-on_password=enabled uuid=44454C4C-3000-1039-804A-C3C04F4E3431
  *-core
       description: Motherboard
       product: 0G1548
       vendor: Dell Computer Corp.
       physical id: 0
       version: A00
       serial: ..CN70821426F098.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05
          date: 12/02/2003
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2800MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff memory:feb80000-febfffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fe900000-feafffff
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: 00:0d:56:69:9d:a2
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.3 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:fe9fe000-fe9fffff memory:fea00000-fea03fff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: IC35L120AVV207-1
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: V24O
             serial: VNVD09G4DA1N5T
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00082055
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f3692715-2094-479d-8572-b4d2e37f1ddc
                size: 107GiB
                capacity: 107GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-09-12 13:42:02 filesystem=ext4 lastmountpoint=/ modified=2013-12-18 11:22:00 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-12-18 11:25:05 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 4391MiB
                capacity: 4391MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4391MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom:0
             description: DVD writer
             product: DVD-RW  DVR-112D
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.15
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw
             configuration: status=nodisc
#
```

---

### Post by mörgæs on 2013-12-20
Several applications use the home folder as a temporary area. Normally I wouldn't worry. 

Is it taking a lot of space?

---

### Post by gfullmer1 on 2014-01-24
It is taking 888,315,904 bytes.  Still haven't found a way to delete it.

---

### Post by Bucky Ball on 2014-01-24
In a terminal:

gksudo nautilus

... if you're using Nautilus as a file browser, if not, replace 'nautilus' with whatever you are using, then delete what you like.

---

### Post by jeanjd63 on 2014-01-24
Hello 
I think you can delete it :
**sudo  rm  -r  "[COLOR=#000000][FONT=Ubuntu Mono]OU-qKRRubG"[/FONT][/COLOR]**

---

