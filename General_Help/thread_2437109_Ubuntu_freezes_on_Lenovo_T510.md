---
title: "Ubuntu freezes on Lenovo T510"
date: 2020-02-18
forum: General Help
---

### Post by andrewknight on 2020-02-18
[LEFT][B][COLOR=#000000][FONT=courier new]Help please.  My laptop freezes unexpectedly and frequently.
I am using a lenovo thinkpad T510 (about 7 years old, bought “factory refurbished” 5 years ago),with Intel® Core™ i5 CPU M 540 @ 2.53GHz × 4 processor, 8 Gb RAM, NVA8 graphics, [/FONT][/COLOR][/B] [/LEFT]
 [LEFT][B][COLOR=#000000][FONT=courier new]running Ubuntu 18.04.4 LTS fully updated.
I am fairly new to Ubuntu (after Windows XP), but can run Libre Office from CLI, and find syslog.  Freezes mean the cursor remains directable, but cannot close programmes, and I cannot open a terminal with CTRL + ALT + Fx. I have to close the system with the power button and reboot.  It has done this when I was using Libre Office (writer) and Videos.[/FONT][/COLOR][/B][/LEFT]
 [LEFT]**[COLOR=#000000][FONT=courier new]I think the following indicates the graphics card (I have had problems using a digital projector and extending the screen with OpenLP software) – is this relevant?[/FONT][/COLOR]**[/LEFT]
 **[COLOR=#000000][FONT=courier new]lspci -nn | grep -E 'VGA|Display'[/FONT][/COLOR]**[LEFT] [B][COLOR=#000000][FONT=courier new]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218M [NVS 3100M] [10de:0a6c] (rev a2)

[/FONT][/COLOR][/B]
[/LEFT]
 [LEFT]**[COLOR=#000000][FONT=courier new]What do I check / change?[/FONT][/COLOR]**[/LEFT]

---

### Post by mörgæs on 2020-02-18
Though you have already posted some hardware details let's see it all.

Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

### Post by andrewknight on 2020-02-19
Thanks.  Here is a copy of the text generated as the lshw.txt file:
```
computer
    description: Notebook
    product: 4349AF5
    vendor: LENOVO
    version: ThinkPad T510
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=ThinkPad T510 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 4349AF5
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 6MET92WW (1.52 )
          date: 09/26/2012
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz
          slot: None
          size: 2402MHz
          capacity: 2534MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid dtherm ida arat flush_l1d cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-through data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: burst internal write-through unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: c
             slot: Internal L3 Cache
             size: 3MiB
             capacity: 8MiB
             capabilities: burst internal write-back
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 2a
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: RMT3160ED58E9W1600
             vendor: Fujitsu
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             vendor: 0000
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 2
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
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
             resources: irq:24 ioport:2000(size=4096) memory:cc000000-cdefffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218M [NVS 3100M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:31 memory:cc000000-ccffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:2000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:cdefc000-cdefffff
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
             configuration: driver=mei_me latency=0
             resources: irq:33 memory:f2427800-f242780f
        *-network
             description: Ethernet interface
             product: 82577LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 06
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:29 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f2428000-f24283ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.3.0-40-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: Integrated Camera
                      vendor: Chicony Electronics Co., Ltd.
                      physical id: 6
                      bus info: usb@1:1.6
                      version: 23.45
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=200mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:f2420000-f2423fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:f2000000-f20fffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6200
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 35
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-40-generic firmware=9.221.4.1 build 25532 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:32 memory:f2000000-f2001fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:3000(size=4096) memory:f0000000-f1ffffff ioport:f2500000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 memory:f2100000-f21fffff
           *-generic:0
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:0d:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f2100000-f21000ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller]
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:0d:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f2100400-f21004ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 PCIe IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:0d:00.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:19 memory:f2100800-f2100fff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:f2428400-f24287ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.3.0-40-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: QM57 Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:1840(size=32) memory:f2427000-f24277ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f2428800-f24288ff ioport:1860(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel ips latency=0
             resources: irq:19 memory:f2426000-f2426fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: 1st Generation Core i3/5/7 Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0001
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=08a727e4
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 731MiB
                capacity: 731MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2020-01-12 19:38:06 filesystem=ext4 lastmountpoint=/boot modified=2020-02-18 20:30:17 mount.fstype=ext4 mount.options=rw,relatime mounted=2020-02-18 16:19:45 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 930GiB
                capacity: 930GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 930GiB
                   capacity: 930GiB
                   width: 512 bits
                   capabilities: encrypted luks initialized
                   configuration: bits=512 cipher=aes filesystem=luks hash=sha256 mode=xts-plain64 version=1
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT30N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: LT10
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: 42T4801
       vendor: Panasonic
       physical id: 1
       slot: Rear
       capacity: 93960mWh
       configuration: voltage=10.8V
```

---

### Post by kc1di on 2020-02-19
Hello, 
Your Graphics card is most likely the culprit.  Nvidia cards need some special care to get working right. 
If your using the open source driver nouveau.  You need to append nomodeset to the boot line of grub. 
You can access the boot grub boot menu on boot as soon as the Lenovo log comes up press and hold the 
shift key and that should bring up the grub menu.  Then hit E to edit the entry - in the boot line.
[this page]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/") will show you how. once booted up you need to either install the Nvidia proprietary driver for your card or make nomodeset default by editing the /etc/default/grub file (as root) and adding the nomodeset like it  says. in answer 126 on the page referenced before. Good luck.

---

### Post by CelticWarrior on 2020-02-19
**'nomodeset' is NOT to be made default**, it's just a workaround that uses a generic video mode instead of the one given by the graphics drivers. It avoids the freeze though and because of that it can be used *temporarily* until the Nvidia drivers are installed.

In order to install the proper drivers the best you can do is to open Additional Drivers, select and install the recommended version then reboot.

---

### Post by mörgæs on 2020-02-20
Your BIOS firmware is the latest so no problems here. 

Applying closed-source Nvidia drivers is an option but you could also try a live boot of something lighter than Ubuntu, say X/Lubuntu 19.10.

---

### Post by andrewknight on 2020-02-21
RESOLVED - at least I think so.
Thank you all for your comments.  Understanding that the video card was likely to be the problem, but also learning that the Ubuntu repository now offered the NVIDIA proprietary driver, I opened the "Software and Updates" app, and then Additional Drivers tab. Clicking on "Using NVIDIA binary driver . . " instead of "Using X.Org X server - Nouveau display . . " - the open source driver, seems to have solved it.  I have used the laptop today for several hours without problems!

---

### Post by mörgæs on 2020-02-21
Good, if it keeps behaving well then please use Thread Tools for marking the thread solved.

---

