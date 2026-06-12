---
title: "Ubuntu 21.04 and 20.04 randomly reboots on my PC"
date: 2022-05-02
forum: General Help
---

### Post by aermak-am on 2022-05-02
[COLOR=#232629][FONT=-apple-system]My PC with installed Ubuntu 20.04 keeps rebooting.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Before 20.04 LTS I had Ubuntu 21.04, which had the same issue, which is why I decided to install previous version.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I tried to ground it in the office. It didn't help. One day, I even took it home from the office, I connected it at home with another power cable. It still rebooted several times. So, probably, it is not static electricity causing reboots.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I tried to run it without video card. It kept rebooting.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I inserted RAMs into different sockets. It kept rebooting.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I plugged my PC into UPS. The same.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I brought it to the service. They tested my PC for two days. They experienced same problem. Their checked hardware, said that it was ok. Installed windows on the same SSD, and there was no reboots with it. Then they somehow upgraded my Ubuntu. I am not sure what they did. But after that, they say, they did not experienced rebooting. However, when I brought it to the office it rebooted again.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I have 32 Gb of RAM, I had 2 Gb of swap which I increased an hour ago to 16 Gb, but it didn't solve problem with reboots. I have a NVIDIA P106-100 graphic card with 6Gb memory.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Time between reboots is random it can be 2 minutes or 12 hours. I am newbie in Linux, so, please, tell me what commands I should execute to provide you with needed information. Thanks for your help and time!

lshw -sanitize prints: 

[/FONT][/COLOR]```
Computer
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.1.1 dmi-3.1.1 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: PRIME B365M-K
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: [REMOVED]
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1202
          date: 08/01/2019
          size: 64KiB
          capacity: 16MiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 32GiB
        *-bank:0
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: TEAMGROUP-UD4-2400
             vendor: Team Group Inc.
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM1
             size: 16GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: TEAMGROUP-UD4-2400
             vendor: Team Group Inc.
             physical id: 1
             serial: [REMOVED]
             slot: ChannelB-DIMM1
             size: 16GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: 40
          slot: L1 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 41
          slot: L2 Cache
          size: 2MiB
          capacity: 2MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 42
          slot: L3 Cache
          size: 12MiB
          capacity: 12MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-9700K CPU @ 3.60GHz
          vendor: Intel Corp.
          physical id: 43
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-9700K CPU @ 3.60GHz
          serial: [REMOVED]
          slot: LGA1151
          size: 4542MHz
          capacity: 4900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=8 enabledcores=8 threads=8
     *-pci
          description: Host bridge
          product: 8th/9th Gen Core 8-core Desktop Processor Host Bridge/DRAM Registers [Coffee Lake S]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0d
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 6th-10th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0d
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:120 memory:f6000000-f6ffffff ioport:e0000000(size=301989888)
           *-display
                description: 3D controller
                product: GP106 [P106-100]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: irq:140 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff
        *-display
             description: VGA compatible controller
             product: CoffeeLake-S GT2 [UHD Graphics 630]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:138 memory:f5000000-f5ffffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:125 memory:f7210000-f721ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.13.0-40-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.13
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 7
                   bus info: usb@1:7
                   version: 39.06
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:1
                   description: Mouse
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 8
                   bus info: usb@1:8
                   version: 2.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.13.0-40-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.13
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
        *-communication
             description: Communication controller
             product: 200 Series PCH CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:137 memory:f722d000-f722dfff
        *-sata
             description: SATA controller
             product: 200 Series PCH SATA controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:126 memory:f7228000-f7229fff memory:f722c000-f722c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f722b000-f722b7ff
        *-pci:1
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #19
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 ioport:2000(size=4096) memory:b8000000-b81fffff ioport:b8200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:3000(size=4096) memory:b8400000-b85fffff ioport:b8600000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:e000(size=4096) memory:f7100000-f71fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 15
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.13.0-40-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:19 ioport:e000(size=256) memory:f7104000-f7104fff memory:f7100000-f7103fff
        *-pci:4
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:f7000000-f70fffff
           *-storage
                description: Non-Volatile memory controller
                product: NVMe SSD Controller 980
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:f7000000-f7003fff
              *-nvme0
                   description: NVMe device
                   product: Samsung SSD 980 500GB
                   physical id: 0
                   logical name: /dev/nvme0
                   version: 1B4QFXO7
                   serial: [REMOVED]
                   configuration: nqn=nqn.1994-11.com.samsung:nvme:980M.2:S64DNF0R605945R state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
                      size: 465GiB (500GB)
                      capabilities: gpt-1.00 partitioned partitioned:gpt
                      configuration: guid=17ae2fda-7e88-4f3d-9939-1f5319ff1680 logicalsectorsize=512 sectorsize=512
                    *-volume:0
                         description: Windows FAT volume
                         vendor: mkfs.fat
                         physical id: 1
                         logical name: /dev/nvme0n1p1
                         logical name: /boot/efi
                         version: FAT32
                         serial: [REMOVED]
                         size: 510MiB
                         capacity: 511MiB
                         capabilities: boot fat initialized
                         configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
                    *-volume:1
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 2
                         logical name: /dev/nvme0n1p2
                         logical name: /
                         version: 1.0
                         serial: [REMOVED]
                         size: 465GiB
                         capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                         configuration: created=2022-04-13 19:46:09 filesystem=ext4 lastmountpoint=/ modified=2022-05-02 22:01:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,stripe=32 mounted=2022-05-02 22:01:35 state=mounted
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: 200 Series/Z370 Chipset Family Power Management Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: latency=0
             resources: memory:f7224000-f7227fff
        *-multimedia
             description: Audio device
             product: 200 Series PCH HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:139 memory:f7220000-f7223fff memory:f7200000-f720ffff
        *-serial
             description: SMBus
             product: 200 Series/Z370 Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:16 memory:f722a000-f722a0ff ioport:f040(size=32)
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0501
          physical id: 2
          capabilities: pnp
          configuration: driver=serial
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 4
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0b00
          physical id: 5
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:05
          product: PnP device INT3f0d
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0c02
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-pnp00:07
          product: PnP device PNP0c02
          physical id: 8
          capabilities: pnp
          configuration: driver=system
     *-pnp00:08
          product: PnP device PNP0c02
          physical id: 9
          capabilities: pnp
          configuration: driver=system
     *-pnp00:09
          product: PnP device PNP0c02
          physical id: a
          capabilities: pnp
          configuration: driver=system
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
[COLOR=#232629][FONT=-apple-system][COLOR=#222222][FONT=Verdana]       capacity: 32768mWh[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]

---

### Post by ajgreeny on 2022-05-02
I wonder if you have a temperature problem with the machine; overheating is sometimes the cause of random unannounced reboots.

Alternatively, the hardware that can also cause this problem is a bad power supply unit so that is something that should be checked, though I have no idea how you can do that.
Do you know if this was part of the checking that was done by your service people?

---

### Post by TheFu on 2022-05-02
It could be anything.  Did you swap different RAM?  Test the RAM for at least 3 day?
Do the system logs provide any hints?  Kernel issues? Stack traces?

BTW, there is little need to have more than 4.1G of swap for any system that doesn't hibernate. Extra would only be used when you load the system well beyond what it can handle and as the system slows down, you'll feel that happening and can take corrective steps - like closing the bloated browser and fat email program.

For example:
```
$ free -mh
              total        used        free      shared  buff/cache   available
Mem:            31G         13G         13G        100M        4.1G         17G
Swap:          4.3G        1.2M        4.3G
```

---

### Post by aermak-am on 2022-05-03
Thanks for advice! I doubt that overheating is a problem, since there is little dust inside a corpus. Psensor shows that hardware temperature is no more than 35 degrees.

I doubt competence of my service provider, but they said that they checked power supply unit. 

Might it be somewhat related to BIOS?

---

### Post by aermak-am on 2022-05-03
I tried to change ram sockets, work with 1 ram unit in different sockets. It didn't help. There were reboots. I didn't find anything worrisome in logs. Though, I am not proficient in reading them and extract clues from there, so I might easily missed something important.

---

### Post by TheFu on 2022-05-03
When searching logs (I don't "read" them), I look for some keywords - error, warning, stack, refused, rejected.  Be certain to search case insensitive.  After finding those terms, I'll jump to a few lines above that in the specific log file to see if it might be related. I'll look at the timestamps - anything within 1-2 seconds could be related.

PCs get short circuits sometimes.  These can be caused by accident scraping or dust. Inside data centers, they carefully filter all the air and ensure the airflow is out of the systems with clean, filtered, air at the intake of the racks. There's a real problem with systems shorting.  [https://www.akcp.com/blog/how-data-centers-should-deal-with-air-contamination/](https://www.akcp.com/blog/how-data-centers-should-deal-with-air-contamination/)  At home, the best we can do is to use foam filters on air intakes for our PCs, clean those yearly and for the smaller particles that get inside the case, vacuum those out yearly.  If you see any dust around slots in a case or on the fans, it is passed time to clean the entire machine.  

I used to live in a place that had dust storms. Huge red clouds could be seen from miles away - it was a flat area. No matter how tightly we'd close up the 80 yr old building, that dust would still find a way inside. It was a mess.

People with furry pets can have a terrible dander issue.  I have dry skin and flake it off too.  I keep a hand vacuum with a little brush to keep the dust off everything.

---

### Post by aermak-am on 2022-05-05
I installed ubuntu 18.04 and it stopped rebooting. Any ideas why?

EDIT: Nevermind. It still reboots. Though rarely.

---

### Post by Seb71 on 2022-05-06
Most likelly it's a hardware problem. Installing various OSes won't fix it.

---

### Post by HermanAB on 2022-05-06
I would boot it it with install media and leave it running.  The install system is very conservative and simple.  If it still reboots, then you very probably do have a HW problem.

---

### Post by aermak-am on 2022-05-11
Thanks to everyone! After replacement of motherboard the problem has gone.

---

