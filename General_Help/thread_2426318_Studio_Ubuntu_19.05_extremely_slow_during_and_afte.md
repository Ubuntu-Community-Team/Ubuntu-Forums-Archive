---
title: "Studio Ubuntu 19.05 extremely slow during and after installation. Pentium 4HT@3.4Mhz"
date: 2019-09-07
forum: General Help
---

### Post by ub-joao on 2019-09-07
Hello everyone,

I installed Studio Ubuntu 19.04 and it's extremely slow and has other problems.
Couldn't find a cause for this and decided to reinstall it, this time
not connecting to the internet while installing and choosing not to use
third party software option to avoid device drivers conflicts. But still no luck.
Besides being slow, selecting GRUB option to boot windows 10 (on /dev/sda4)
won't work and PC will restart.

As a workaround, I use GRUB4DOS while booting from my HBCD (Hyren's Boot CD)
and select :
- Boot HDD1 MBR - Ubuntu's GRUB menu will appear but booting STUDIO UBUNTU still takes 15min!
- Boot HDD1 MBR - Ubuntu's GRUB menu will appear. I select "Advanced options for Ubuntu",
then I select "Recovery Mode". Inside "Recovery Mode" menu, I select "System
Information", go back and in the "Recovery Mode" menu, I choose to resume
booting. It works and Ubuntu runs normally. All this process takes me about 1:40 sec including,
logging in and full load of XFCE task bar. Weird is that if I don't use HBCD first,
Studio Ubuntu still boots and runs very slowly
- Boot HDD1 Partition 4 - windows 10 boots directly
- Boot HDD1 MBR - GRUB menu will appear and the option of booting Windows 10 works;

My desktop is old but still enough to run Windows 10 perfectly.
Motherboard is an old Intel D915GAG with Pentium 4HT bit CPU running at 3.4GHz
and has 4GB RAM. Only problem is the graphics card which is onboard and is not
supported by windows 10, so I'm using generic drivers.

On Ubuntu recovery mode I also reseted GRUB but still doesn't solve.
When Ubuntu is slowed, I struggled to run task manager or "top" but there's
no process that overload the CPU.

I don't have a clue for what is causing this but at least I know that is not the hardware
requirements. If anyone could help I would appreciate. Thank you

---

### Post by Autodave on 2019-09-07
Please give us info on your system.

---

### Post by ub-joao on 2019-09-07
Thank you for replying.
I used the following command to extract system information. Hope it's enough
$ sudo lshw -sanitize


```
computer
    description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2019-04-12 08:46+0000X-Generator: Launchpad (build 18920)
    vendor: OEGStone
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 smp vsyscall32
    configuration: boot=normal uuid=[REMOVED]
  *-core
       description: Motherboard
       product: D915GAG
       vendor: Intel Corporation
       physical id: 0
       version: AAC64123-501
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: EV91510A.86A.0482.2006.0222.2350
          date: 02/22/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) 4 processor
          serial: [REMOVED]
          slot: J2E1
          size: 3400MHz
          capacity: 3400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl cpuid pni dtes64 monitor ds_cpl est cid cx16 xtpr pti cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 40
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: [REMOVED]
             slot: J6G1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: [REMOVED]
             slot: J6G2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: [REMOVED]
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: [REMOVED]
             slot: J6H2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:ffa00000-ffafffff memory:cff00000-cfffffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:ff480000-ff4fffff ioport:ec00(size=8) memory:d0000000-dfffffff memory:ff440000-ff47ffff memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:24 memory:ff43c000-ff43ffff
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:ff600000-ff6fffff ioport:cfb00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:ff700000-ff7fffff ioport:cfc00000(size=1048576)
        *-pci:3
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:ff800000-ff8fffff ioport:cfd00000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:4000(size=4096) memory:ff900000-ff9fffff ioport:cfe00000(size=1048576)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.0.0-13-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:cc00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.0.0-13-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 5.00
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.0.0-13-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.00
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@4:1
                   version: 54.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.0.0-13-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 5.00
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ff43bc00-ff43bfff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-13-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: Generic USB device
                   product: 802.11 n WLAN
                   vendor: Ralink
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.01
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:ff500000-ff5fffff ioport:cfa00000(size=1048576)
           *-network
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: enp6s8
                version: 01
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:ff500000-ff500fff ioport:bc00(size=64)
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm pci_native_mode_controller__supports_both_channels_switched_to_isa_compatibility_mode__supports_bus_mastering bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:e800(size=8) ioport:e400(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d800(size=16)
        *-serial
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:19 ioport:c400(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: CD-R/CD-RW writer
             product: CD-RW  CRX230EE
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/sr0
             version: 2YS3
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500312CS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: SC13
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=2b7e7ae6
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 146GiB
                capacity: 146GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2019-09-06 18:25:38 filesystem=ext4 lastmountpoint=/ modified=2019-09-07 13:09:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-09-07 13:01:23 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 146GiB
                capacity: 146GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2019-08-29 18:39:09 filesystem=ntfs label=WIN10_x86US state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 84GiB
                capacity: 84GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-05-04 04:24:57 filesystem=ntfs label=DATABOOT state=clean
           *-volume:3
                description: Windows NTFS volume
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: [REMOVED]
                size: 87GiB
                capacity: 87GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2006-04-28 15:51:31 filesystem=ntfs label=WINXP_PRO state=clean
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlx7cdd902e71d1
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=5.0.0-13-lowlatency firmware=0.36 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11
```

---

### Post by wildmanne39 on 2019-09-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Autodave on 2019-09-07
That Pentium4 is quite old: I am surprised that Win10 even works on there.  I am assuming that Win10 is even slower than Ubuntu Studio.

I know that there are a lot of posts here about issues with 19.04.  If that were my machine, I would try 18.04 since that is a long term service release (LTS).

Did you install the 32 bit or 64 bit system?  That particular CPU is a single core with hyper-threading which kinda allows it to act like a dual core.  I have found, on the couple of machines like that, that I have installed Linux onto, that the 32 bit runs better.

---

### Post by ub-joao on 2019-09-07
I know for sure it's not a requirements problem. If I don't get a solution here, I'll
do as you suggested and install Ubuntu 18.04 64bit/32bit.

I had Windows 7 installed before, it even supported the onboard intel Graphics card but it's going to end support next year.
Then I changed recently to Windows 10. Unfortunately I had to install Windows 10 32 bit and not Windows 10 64bit
because it requires support for PREFETCHW and LAHF/SAHF instructions and my Pentium 4 HT CPU doesn't.

None of Windows 10 or Studio Ubuntu (with HBCD/GRUB4DOS weird trick) run slow. I don't run games that require
3D acceleration, so desktop is perfect for Web browing (Firefox) and Office (LibreOffice). Besides I optimized the
system to run faster. 

I noticed another thing: when I boot in this order:
HBCD (Hirens Boot CD) >> GRUB4DOS inside HBCD >> BOOT HDD1 MBR >> UBUNTU GRUB
OTHER UBUNTU OPTIONS >> RECOVERY MODE >> RESUME BOOT
most of the time shows a message
"disabling #irq 19".

When doesn't show this message UBUNTU boots with normal speed.

using the command 
$sudo lspci -v

```
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [PCI native mode controller, supports both channels switched to ISA compatibility mode, supports bus mastering])
    Subsystem: Intel Corporation D915GAG Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at e800 [size=8]
    I/O ports at e400 [size=4]
    I/O ports at e000 [size=8]
    I/O ports at dc00 [size=4]
    I/O ports at d800 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
    Flags: medium devsel, IRQ 19
    I/O ports at c400 [size=32]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
```

So, it seems irq #19 is reserved for SATA controller.

When Ubuntu is running normally the HDD's benchmark is

$sudo hdparm -tT /dev/sda

```
/dev/sda:
 Timing cached reads:   1862 MB in  2.00 seconds = 932.23 MB/sec
 Timing buffered disk reads: 320 MB in  3.00 seconds = 106.61 MB/sec
```

When Ubuntu is running extremely slow the HDD's benchmark is
$sudo hdparm -tT /dev/sda

```
/dev/sda:
 Timing cached reads:   1506 MB in  2.00 seconds = 752.91 MB/sec
 Timing buffered disk reads:  28 MB in  3.03 seconds =   9.23 MB/sec
```

Another thing I noticed is that the HDD is set as UDMA6 and my motherboard
recognises the disk as UDMA5, most probably because as an old motherboard
it only supports up to UDMA5. When I try to change to UDMA it gives an error:

$sudo hdparm -Xudma5 /dev/sda

```
/dev/sda:
 setting xfermode to 69 (UltraDMA mode5)
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 12 00 00 00 00 24 00 00 c0 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```




Thank you

---

### Post by pcfan1234 on 2019-09-07
I recommend Lubuntu or Xubuntu for such an old system.
You CPU supports amd64, so use that image. i386 is dead with 19.10, finally dead.
I have a system with Pentium 4 670 and i915G too, it runs perfectly with Lubuntu 18.04 amd64.
Use htop to check if the problem is the cpu limit (sometimes caused by missing 3D acceleration for GUIs).
The disk usage can be checked with iotop.

---

### Post by mörgæs on 2019-09-08
Here are some ideas for [speeding up Buntu]("https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289").

---

### Post by ub-joao on 2019-09-08
Shame. It seems I won't get a precise answear here for the cause and a solution. I was trying to avoid more endless investigation and reinstalling other versions of Linux. I was hoping somebody would tell me an easy fix like a setting in BIOS. Thank you for the answears but I had a feeling I was misunderstood. The requirements of my my desktop are fine for my needs. It's not slow FOR ME. It has this bug which makes it slow and I can use the lengthly trick I explained of using HBCD to run on good speed. However I don't want to go through that on regular basis and will install 18.04 LTS and hopefully will work.

Thank you

---

### Post by mörgæs on 2019-09-08
Your graphics card can't keep pace with rest of the system. 

I suggest that you take a look at which cards you can get for &#8364; 10 on the second hand marked. This may come in handy: [https://www.videocardbenchmark.net/low_end_gpus.html](https://www.videocardbenchmark.net/low_end_gpus.html)

Your processor and memory are fine (and faster than most of my equipment). For a small amount you can get a big improvement.

---

### Post by ub-joao on 2019-09-08
Funny you mentioned that. I almost won a bid on Ebay on a powerful graphics card a month ago based on that website for about £10. I will buy one eventually. For web & office the onboard card is fine. However windows 10 doesn't support it and there's drop of framerate in watching videos.

 But still, the problem seemed to be related to a hard drive conflict.

---

### Post by CatKiller on 2019-09-08
> **ub-joao said:**
> 
most of the time shows a message
"disabling #irq 19".

When doesn't show this message UBUNTU boots with normal speed.

*That* seems like a shonky BIOS implementation. No shortage of those, particularly in the P4 era.

There are a bunch of kernel options to try to help get around buggy BIOS signalling; IRQ polling, Message Signalled Interrupts, ignoring parts of the APIC, and so on. Fiddling with some of those might help you. Some of them are listed [here](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options).

---

### Post by ub-joao on 2019-09-10
Thanks. Saved that Html for future reference, maybe for next year when I'll install next Ubuntu 20.04 LTS.

For now, I gave up on 19.04 and installed 18.04 LTS AMD64 and is working fine and fast. A bit disappointed on
the outdated software, specially on GIMP 2.8.22 (I wanted 2.10.12). Installed new repository, SNAP and FLATPAK
versions but got disappointed as well. The added repository ppa:otto-kesselgulasch/gimp still produces one depency problem
with libmypaint which forced me to remove mypaint entirely. As for SNAP and FLATPAK, it's a headache to
install plugins for example. Had enough and set everything to 18.04 versions. I'll be patient and wait for 20.04 LTS.

---

### Post by mörgæs on 2019-09-10
I would advise against Snap and Flatpak. Tend to slow down the system. 

The idea behind LTS is stability, that is the opposite of upgrades. Hence, old software. 

If you want help with installing 19.04 with its selection of upgraded software then please describe the exact problems. It has worked fine for me.

---

### Post by Yellow Pasque on 2019-09-11
In addition to the parameters CatKiller linked to, I'd suggest to try booting with 'noirqdebug' and see if the message about disabling IRQ 19 (and the slowness) goes away.

---

