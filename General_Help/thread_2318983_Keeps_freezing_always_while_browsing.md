---
title: "Keeps freezing always while browsing"
date: 2016-03-31
forum: General Help
---

### Post by tellll on 2016-03-31
I'm using currently ubuntu 14.04 LTS and idk why it keeps freezing all the time while browsing, it doesn't matter if it's firefox or chrome, I just did a clean install and it freezed after like 10 minutes, I was just about to download chrome and it freezed.

I tried during this last days xubuntu and ubuntu mate and the same thing happened. idk what's going on. I like ubuntu and I need it for some work but uff.

Please help.

---

### Post by tellll on 2016-03-31
Just happened again, and this is the syslog:
> \00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00

before this there's a ufw log, could ufw be freezing my laptop?
> Mar 31 20:00:44 ubuntu kernel: [ ] [UFW BLOCK]

---

### Post by RobGoss on 2016-04-01
Hello and welcome, in order to get best possible answer please provide use with the specifications for the machine in question.

---

### Post by tellll on 2016-04-01
This is what** lshw **shows:

```




```

Or how can I go back to ubuntu 14.04.3.. that version worked fine?

---

### Post by gabriel69 on 2016-04-01
I think I have the same problem... try a fresh install without Google Chrome and see if it's not crashing. I'm testing right now.

---

### Post by tellll on 2016-04-02
I did that yesterday, no google chrome and it crashed. But I just installed **mesa-utils** two hours ago and no crashes so far, still testing, though.
Edit: Nah nvm, guess I'l try mint.

---

### Post by RobGoss on 2016-04-02
> **tellll said:**
> This is what** lshw **shows:

```
ubuntu                        description: Notebook
    product: HP Pavilion 11 x360 PC
    vendor: Hewlett-Packard
    version: 0977100000405010420180
    serial: CN6ZZ5
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV X=MIN sku=F4H26LA#ABM uuid=D9589E8F-6DFE-11E4-B2A0-ECB1D7DC53B1
  *-core
       description: Motherboard
       product: 2209
       vendor: Hewlett-Packard
       physical id: 0
       version: 57.48
       serial: PEQADC21T7QMXE
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.24
          date: 01/07/2015
          size: 64KiB
          capacity: 4544KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU  N3540  @ 2.16GHz
          slot: CPU 1
          size: 1347MHz
          capacity: 1347MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=1
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 5
          slot: Unknown
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 4GiB
        *-bank
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: M471B5173DB0-YK0
             vendor: Samsung
             physical id: 0
             serial: 571622
             slot: Bottom
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:266 memory:90000000-903fffff memory:80000000-8fffffff ioport:2050(size=8)
        *-storage
             description: SATA controller
             product: Atom Processor E3800 Series SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0e
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:262 ioport:2048(size=8) ioport:205c(size=4) ioport:2040(size=8) ioport:2058(size=4) ioport:2020(size=32) memory:90a1e000-90a1e7ff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:261 memory:90a00000-90a0ffff
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:265 memory:90900000-909fffff memory:90800000-908fffff
        *-multimedia
             description: Audio device
             product: Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:267 memory:90a10000-90a13fff
        *-pci:0
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096)
        *-pci:1
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:90700000-907fffff
           *-network
                description: Wireless interface
                product: RT3290 Wireless 802.11n 1T/1R PCIe
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=4.2.0-34-generic firmware=0.37 ip=192.168.1.87 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:90710000-9071ffff
           *-generic UNCLAIMED
                description: Bluetooth
                product: RT3290 Bluetooth
                vendor: Ralink corp.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:90700000-9070ffff
        *-pci:2
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:5000(size=4096) memory:90600000-906fffff
           *-generic
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:263 memory:90600000-90600fff
        *-pci:3
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:1000(size=4096) memory:90500000-905fffff ioport:90400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 07
                serial: 
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:264 ioport:1000(size=256) memory:90500000-90500fff memory:90400000-90403fff
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial UNCLAIMED
             description: SMBus
             product: Atom Processor E3800 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:90a18000-90a1801f ioport:2000(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS545050A7
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A350
             serial: RBF50HA4R
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=d8e61954-4dc7-410e-a409-94b0e4fb8380 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 36014c1
                size: 448MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-03-30 07:06:57 filesystem=ntfs label=Recovery modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: 7a07468
                size: 93MiB
                capacity: 99MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: e0dee28f-b245-400e
                capacity: 15MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 9a2080f8-1826-534848-a0324
                size: 249GiB
                capacity: 249GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2016-03-30 07:07:10 filesystem=ntfs name=Basic data partition state=clean
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: 788c-c
                size: 799MiB
                capacity: 805MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-03-30 12:11:15 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:5
                description: EXT4 volume
                vendor: Linux
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                logical name: /
                version: 1.0
                serial: 3e70-e1670e703833
                size: 211GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-03-30 22:44:56 filesystem=ext4 lastmountpoint=/ modified=2016-04-01 17:16:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-04-01 17:16:41 state=mounted
           *-volume:6
                description: Linux swap volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                version: 1
                serial: 76b5fb2-d1dd9f6cb555
                size: 3982MiB
                capacity: 3982MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
  *-battery
       product: PL02029
       vendor: 33-23
       physical id: 1
       version: 01/01/2013
       serial: DummySerialNumber
       slot: Primary
       capacity: 30096mWh
       configuration: voltage=7,2V
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh



```

Or how can I go back to ubuntu 14.04.3.. that version worked fine?


Well it seems like your specs are in order so I'm not sure why your system is continuing to freeze as so. Have you try another distro to see if it freezes?

As far as going back to 14.04 did you have a complete backup of that installation? that's the only way I know with out install a new installation

---

### Post by mörgæs on 2016-04-02
We are dealing with a Bay Trail processor so I suggest installing 16.04.

---

### Post by tellll on 2016-04-02
> **RobGoss said:**
> Well it seems like your specs are in order so I'm not sure why your system is continuing to freeze as so. Have you try another distro to see if it freezes?

As far as going back to 14.04 did you have a complete backup of that installation? that's the only way I know with out install a new installation
I'll try mint today

> **mörgæs said:**
> We are dealing with a Bay Trail processor so I suggest installing 16.04.
I tried installing the beta 2 yesterday but got an error. *[SIZE=4][FONT=system]ubi-prepare failed with exit code 255[/FONT][/SIZE]*

---

### Post by mörgæs on 2016-04-03
Don't install the beta. The daily build is a better option.

---

### Post by tellll on 2016-04-03
> **mörgæs said:**
> Don't install the beta. The daily build is a better option.
Guess I'm done with ubuntu for now, just installed the daily build this morning and it freezed. Windows works fine, I wanted to use ubuntu but I guess I'll try mint next week. Thanks for your help.

---

### Post by mörgæs on 2016-04-03
Yes, new hardware is sometimes not completely supported. I hope you get back to Buntu one day when the software has caught up.

---

### Post by RobGoss on 2016-04-03
> **tellll said:**
> I'll try mint today


I tried installing the beta 2 yesterday but got an error. *[SIZE=4][FONT=system]ubi-prepare failed with exit code 255[/FONT][/SIZE]*

Since Ubuntu 16.04 has been introduced I've been successful with 2- installations in fact it's running so well I cloned both systems for not in case I run into any problems. Not this method may not be for everyone but I find it easy to work with Ubuntu even if there are a few bugs in a distro.

If you really want to get the feel of Ubuntu I wouldn't give up but that's just me :)

---

### Post by mörgæs on 2016-04-04
I just stumbled upon a [post]("http://ubuntuforums.org/showthread.php?t=2319389&p=13465276&viewfull=1#post13465276") which might shed some light on the Bay Trail problem.

---

### Post by tellll on 2016-07-25
I'll just leave here my solution.

I followed [this video]("https://www.youtube.com/watch?v=CokrHUykkUQ") and upgraded my kernel to the last release and now ubuntu is working just fine, hope this can help someone else.

Edit: Just wanted to update my answer, my solution above just delays the freeze from a couple of minutes to some hours.

---

