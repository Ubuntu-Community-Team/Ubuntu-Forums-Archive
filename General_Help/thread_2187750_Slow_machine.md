---
title: "Slow machine"
date: 2013-11-13
forum: General Help
---

### Post by Otto-C on 2013-11-13
Dual boot with Ubuntu 12.04.4 and Windows XP on Dell desktop.

Some time in the last 2 months following an update the computer
has slowed down considerabley on the internet on the Ubuntu side.
Have checked the Windows side and the internet runs normally.
Have also inquired of the ISP and they advise its not them.
I am not knowledgable enough but could something have happened
to the ethernet driver and could it be reinstalled?
How to work with this problem?

tia
otto-c

---

### Post by stefbeukers on 2013-11-14
Do you use Jupiter for power saving?

---

### Post by Otto-C on 2013-11-14
I just have a straight forward install.
Do not know what Jupiter is.

---

### Post by sudodus on 2013-11-14
Please describe your hardware, particularly for the internet connection. That will provide clues for us to give tips and advice.

- Have you got wired or wireless internet from the computer?
- What chip/card? What driver is used? (check with for example the program ***hardinfo***)

- Is there a router?

---

### Post by Otto-C on 2013-11-14
Will get info requested tomorrow and will post.

---

### Post by Otto-C on 2013-11-15
Connection is via ethernet only.
Software for ethernet controller is what came with the install.

Did [www.speedtest.net]("http://www.speedtest.net") for:
            *  Ping Ms   **     Download  Mbps  **   Upload  Mbps

Win. Xp *   0            **     28.82                 **   5.95
Ubuntu  *  89           **     17.71                 **   2.24

Comcast Arris modem model wbm760
Linksys Wirelsss G 2.4 54mbps

Tried to install HARDINFO.  It fails.

Below 'lspci' and 'lshw'.

~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
~$ 


```
greg@greg-desktop:~$ sudo lshw
greg-desktop             
    description: Desktop Computer
    version: OEM
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=44454C4C-5200-1035-8044-C2C04F584431
  *-core
       description: Motherboard
       product: 0CU409
       vendor: Winbond Electronics
       physical id: 0
       version: &#65533;&#65533;&#65533;
       serial: ..CN7360478N059L.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: 1.0.3
          date: 07/12/2007
          size: 128KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4400  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: HYMP564U64BP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: 0000302E
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: 64T64000HU25FB
             vendor: Infineon (Siemens)
             physical id: 1
             serial: 010AEB16
             slot: DIMM2
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: HYMP564U64BP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             serial: 0000402D
             slot: DIMM3
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: M3 78T6553CZ3-CE7
             vendor: Samsung
             physical id: 3
             serial: 03169872
             slot: DIMM4
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 2GHz
          capacity: 2GHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:fde00000-fdefffff ioport:fda00000(size=1048576)
        *-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff memory:fdb00000-fdbfffff
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:1a:a0:98:4d:7a
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.1-2 ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fd00(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fc00(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fb00(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fdffe000-fdffe3ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:fdff4000-fdff7fff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fa00(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:f900(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f800(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdffd000-fdffd3ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=8) ioport:f400(size=4) ioport:f300(size=16) ioport:f200(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800JD-75MS
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WMAM9VA29482
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0f4738c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 34a7404c-3e0e-c64c-b8df-49fc750e07e9
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-09-30 11:57:49 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 33GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1517MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW GSA-H73N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: B103
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffc000-fdffc0ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f000(size=8) ioport:ef00(size=4) ioport:ee00(size=8) ioport:ed00(size=4) ioport:ec00(size=16) ioport:eb00(size=16)

```

---

### Post by sudodus on 2013-11-17
> **Otto-C said:**
> Connection is via ethernet only.
Software for ethernet controller is what came with the install.

Did [www.speedtest.net]("http://www.speedtest.net") for:
            *  Ping Ms   **     Download  Mbps  **   Upload  Mbps

Win. Xp *   0            **     28.82                 **   5.95
Ubuntu  *  89           **     17.71                 **   2.24

Comcast Arris modem model wbm760
Linksys Wirelsss G 2.4 54mbps

~$ lspci
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
[/CODE]

Did you use the Linksys Wireless (and not the Intel Ethernet controller)? In that case ***maybe*** there is some problem with a new driver for that device, or some bad setting. Please test when booted from a CD/DVD/USB install drive 'Try Ubuntu, do not install', and check what speed you get with the fresh settings of the original version of the iso file :-)

---

### Post by Otto-C on 2013-11-18
Did as you suggested used a 12.04.2 DVD.  The regular user thought the screens came up
faster than installed version.  Tried his opinion of the installed version and he could not tell
a difference. We did a speedtest and the numbers were down from the earlier test those
being:
ping ** download **  upload
13   **  10.15      **  4.08
Will try more extensive test tomorrow as well as any suggestion you may have. The machine
has no wireless capability.

---

### Post by sanderj on 2013-11-18
You have 1GB RAM, haven't you?

What is the output of 'uptime' (last three numbers)

What if you boot Lubuntu 12.04?

---

### Post by sudodus on 2013-11-19
> **Otto-C said:**
> Did as you suggested used a 12.04.2 DVD.  The regular user thought the screens came up
faster than installed version.  Tried his opinion of the installed version and he could not tell
a difference. We did a speedtest and the numbers were down from the earlier test those
being:
ping ** download **  upload
13   **  10.15      **  4.08
Will try more extensive test tomorrow as well as any suggestion you may have. The machine
has no wireless capability.

The speed test also depends on the network outside the computer and outside the house (the internet). So the results will be different as you can see when repeating from exactly the same system. If you test several times, you get a better notion (and maybe use some statistical methods).

-o-

I agree with ***sanderj*** that you should try a system with a lighter desktop environment. Standard Ubuntu with Unity need at lot of memory only to run the desktop itself. Unfortunately Lubuntu 12.04 has passed end of life, so it would be a better idea to switch to Xubuntu 12.04 LTS, which should also run well with 1 GB RAM. (It's OK to test Lubuntu 12.04, but do not install it, because there will be no security updates of the desktop specific program packages.)

---

### Post by Otto-C on 2013-11-21
Sorry it took a little longer to get back. Regular user of machine not available.
It appears doing live DVD fixed the problem and I should have more thoroughly
checked the results.
Today checked the speedtest numbers and the machine is up to full speed.
**         **ping ** download ** upload
before
update  **13    ** 29.34       ** 5.22
after
update  **13    ** 30.32       ** 4.56

Thanks so much for solving this problem.

---

### Post by sudodus on 2013-11-21
You are welcome :-)

---

