---
title: "Brightness on HP Pavilion DV6"
date: 2013-12-09
forum: General Help
---

### Post by amjjawad on 2013-12-09
Hi,

Dual Booting System:
Windows 7
Xubuntu 12.04.3 

Installed on HP Pavilion DV6 Laptop (Core i5 1st generation): 

```
lshw
hp-pavilion-dv6           
    description: Notebook
    product: HP Pavilion dv6 Notebook PC (XS080EA#ABV)
    vendor: Hewlett-Packard
    version: 0588110000242D10010020100
    serial: CNF035BH2S
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=XS080EA#ABV uuid=434E4630-3335-4248-3253-60EB691B64D5
  *-core
       description: Motherboard
       product: 144A
       vendor: Hewlett-Packard
       physical id: 0
       version: 65.38
       serial: PL61K011ZZB1MT
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.29
          date: 11/07/2011
          size: 1MiB
          capacity: 1472KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd  int13floppynec int13floppytoshiba int13floppy360 int13floppy1200  int13floppy720 int13floppy2880 int9keyboard int10video acpi usb  biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 13
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          slot: CPU
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr  pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx  fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon  pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64  monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2  popcnt lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid  cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L3 cache
             physical id: 14
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 16
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 17
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 15
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5273CH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 844016BE
             slot: Bottom - Slot 1
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns) [empty]
             physical id: 1
             serial: 00000000
             slot: Bottom - Slot 2
             width: 8 bits
             clock: 1067MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
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
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:c4400000-c44fffff ioport:a0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:44 memory:a0000000-afffffff  memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
           *-multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5000 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:47 memory:c4420000-c4423fff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:c4504000-c450400f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c450a000-c450a3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:c4500000-c4503fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:c3400000-c43fffff ioport:c0400000(size=16777216)
           *-network
                description: Wireless interface
                product: RT3090 Wireless 802.11n 1T/1R PCIe
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 70:f3:95:71:ae:8e
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci  driverversion=3.2.0-57-generic firmware=0.34 ip=x.x.x.x latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:c3400000-c340ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:c2400000-c33fffff ioport:c1400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: 60:eb:69:1b:64:d5
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master  cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt  1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=r8169 driverversion=2.3LK-NAPI duplex=half  firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII  speed=10Mbit/s
                resources: irq:42 ioport:2000(size=256)  memory:c1404000-c1404fff memory:c1400000-c1403fff  memory:c1410000-c141ffff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:c4509000-c45093ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:5048(size=8) ioport:505c(size=4)  ioport:5040(size=8) ioport:5058(size=4) ioport:5020(size=32)  memory:c4508000-c45087ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BEKT-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX71C5074335
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=078c2322
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 040b-a940
                   size: 197MiB
                   capacity: 199MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-12-10 04:24:14 filesystem=ntfs label=SYSTEM state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 60993161-0877-bd4c-9370-657dcdee98ea
                   size: 199GiB
                   capacity: 200GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-12-10 04:24:21 filesystem=ntfs label=Win7 state=clean
              *-volume:2
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: FAT32
                   serial: 0ca8-c80d
                   size: 95MiB
                   capacity: 103MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 265GiB
                   capacity: 265GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 20GiB
                      configuration: mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered  state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 100GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 4098MiB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 141GiB
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT30L
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: mP04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c4506000-c45060ff ioport:5000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:19 memory:c4507000-c4507fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:7f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:7f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:7f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:7f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:7f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:7f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: MU06055
       vendor: Conexant (Rockwell)
       physical id: 1
       slot: In the back
       capacity: 5100mWh
       configuration: voltage=10.8V


```

This Laptop has some issues/problems with 'Linux' only as the very same issues/problems don't exist with Windows 7

1- Most of the time, I can NOT control the brightness level of my display/monitor (can not increase nor decreaase)
2- Some other time, I can but whenever I increase the brightness level, I can not change it after that neight to decrease it nor increase it
3- Whenever I reboot, the brightness level are not saved
4- I control the brightness level on F2 and F3 Keys on the Kebboard - with HP Pavilion DV6, you don't need to use Fn, just press either F2 or F3 to change brightness level. I don't know yet a way to change the brightness level from within the system (Xubuntu)?

You see, the brightness is a pain with this machine whenever I use Linux (Ubuntu based system).
On the very same machine, Windows 7 is installed (as purchased) and everything is working just fine but of course, I can't use Windows anymore, Linux in the blood now :)


Any idea how to solve this?
As mentioned earlier, this laptop is giving me hard time with 'Linux' only. So far, this is the 3rd issue (have some other different problems) but I'd like to fix these issues once and for all.

Thank you!

---

### Post by varunendra on 2013-12-12
Hello amjjawad !

Have you tried any [boot parameters]("https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options") yet? Like "i915.modeset=1"?
Or manually setting the value of brightness in "/sys/class/backlight/*<your primary video adapter>*/brightness" ?

If unsure about these, I'd like to take a look at the output of -
```
for i in `ls /sys/class/backlight/`; do echo -e "\n $i"; cat /sys/class/backlight/$i/{brightness,max_brightness,actual_brightness}; done
```

---

