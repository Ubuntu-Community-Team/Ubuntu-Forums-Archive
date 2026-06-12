---
title: "Completely random freezes"
date: 2014-12-04
forum: General Help
---

### Post by ughahaven on 2014-12-04
I'm not sure where exactly to post this, but it started with Ubuntu and I'd like to eventually at least try out Ubuntu before deciding on my
distro, so here it is.
As most of you are as well, I've ended up being the local "tech guy" for my friends and extended family. As a result, I've been given many old
computers, printers and the like.


Recently I was given a fairly decent older system, an Acer Aspire E360 with a copy of winXP on it.


I'd like to use this as my secondary computer, basically a hardware and software test bed so I can try out some parts from older systems with
no risk of frying my main rig.


Also I haven't used linux in many years and I'd like to tinker around with it again.


So I tried installing ubuntu 14.04 from a disc, it installed ok but after first install the mouse froze and i could only use keyboard input
for a few seconds. After that, the entire system froze and wouldn't respond at all. I rebooted a few times and sometimes it wouldn't get through
boot and sometimes it froze seconds after restart.


I then tried several other distros, almost all based on Ubuntu with almost the exact results. A few differed though.


(All of these were installed using a 4GB flash drive via Universal USB Installer version 1.9.5.8)
Linux Mint 17.1 Cinnamon: Live session ran fine for 1-5 minutes then froze in almost exactly the same way.
Puppy Linux Tahr: Sometimes ran fine for an hour, but then froze. Other times froze in seconds.
Ubuntu 14.04 Again: Tried it via USB to see if it was my disc. Live session froze in seconds after boot.
Bodhi Linux: Seems to run fine. I tested it for about an hour. No issue as far as I could see.
ElementaryOS Luna: Perfect, super fast. No freezes or problems.
Mini XP: Not linux, but I figured I'd mention I ran it from Hiren's Boot disc and I had no problems at all.
Reinstall of XP: Went fine, No crashes.


As far as I know, all of the linux distros are based on the latest Ubuntu. So its got to be something that Mint, Puppy and Ubuntu have in
common that Bodhi and Elementary DOESN'T have.


I'm not super knowledgable on linux, (which is why I want this comp to tinker with) but could there be some kinda problem with gnome/unity
that's been carried over to the other distros?


Here's the specs to the Acer as best as I can find:
[http://www.cnet.com/products/acer-aspire-e360-2-0-ghz-athlon-x2-1gb-ddr/specs/](http://www.cnet.com/products/acer-aspire-e360-2-0-ghz-athlon-x2-1gb-ddr/specs/)


However, linux is reporting its an Nvidia graphics chip, whereas those specs say its ati. Not sure which is true as I'm using the onboard
graphics.

I'm more than willing to post any logs or install anything I need to. Teach me oh wise ones! I bow before your knowledge :)

---

### Post by mörgæs on 2014-12-04
Welcome to the fora.

In order to find your exact hardware please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by ughahaven on 2014-12-04
Since I currently have Elementary installed (and it seems to be the best as far as not actually freezing) I ran it on that. I hope that's ok.
Here you go:

```
computer    description: Computer
    product: Aspire E360
    vendor: Acer
    version: R02-B0
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal cpus=2 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: FC51GM
       vendor: Acer
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: R02-B0
          date: 06/13/2006
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          version: 15.11.1
          slot: Socket 939
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache:0
          description: L1 cache
          physical id: 3
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: 5
          slot: External Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR
             physical id: 1
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM DDR [empty]
             physical id: 2
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM DDR [empty]
             physical id: 3
             slot: A3
             width: 64 bits
     *-cpu:1
          physical id: 6
          bus info: cpu@1
          version: 15.11.1
          size: 1GHz
          capacity: 1GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: NVIDIA Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: NVIDIA Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: NVIDIA Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: NVIDIA Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: NVIDIA Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdb00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:b000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C51G [GeForce 6100]
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:16 memory:fc000000-fcffffff memory:d0000000-dfffffff memory:fb000000-fbffffff memory:40000000-4001ffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: NVIDIA Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:9000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
             vendor: Texas Instruments
             physical id: 6
             bus info: pci@0000:03:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
             resources: irq:19 memory:fddff000-fddff7ff memory:fddf8000-fddfbfff
     *-multimedia
          description: Multimedia audio controller
          product: MCP51 AC97 Audio Controller
          vendor: NVIDIA Corporation
          physical id: 10.2
          bus info: pci@0000:00:10.2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=snd_intel8x0 latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:c800(size=256) ioport:c400(size=256) memory:fe02b000-fe02bfff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a1
          serial: [REMOVED]
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=[REMOVED] latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
          resources: irq:23 memory:fe02a000-fe02afff ioport:c000(size=8)
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
     *-scsi:0
          physical id: d
          bus info: usb@1:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: SanDisk Cruzer
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 8.02
             serial: [REMOVED]
             size: 3835MiB (4022MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sda
                size: 3835MiB (4022MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   vendor: SYSLINUX
                   physical id: 1
                   logical name: /dev/sda1
                   logical name: /cdrom
                   version: FAT32
                   serial: [REMOVED]
                   size: 3832MiB
                   capacity: 3832MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 11
          bus info: usb@1:6
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@3:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@3:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@3:0.0.3
             logical name: /dev/sde



```

---

### Post by mörgæs on 2014-12-04
Hardware looks fine. 
Have you tried running **memtest** for a couple of hours?

---

### Post by ughahaven on 2014-12-04
I ran it through a complete pass first thing, no problems. I'll run it some more and see if anything turns up after more passes.

Anything else I can do?

---

### Post by tgalati4 on 2014-12-04
Check your power supply, either in BIOS in "Health Monitoring" or use a voltmeter.  5VDC and 12VDC are critical to PC operation.

---

### Post by ughahaven on 2014-12-05
PC health status is showing:
CPU Vcore is 1.39V
+3.3V is 3.28V
+5V is 5.08V
+12V is 11.90V
+5VSB is 4.99V
Voltage Battery is 2.86V
CPU temp is 43c/109f
System temp is 37c

I checked a molex connector in case with my meter and it reads 5.14v for the red wire and 11.98 for the yellow wire.
As far as I know that's all within specs.

Anything look wrong to you guys?

Edit: I ran 8 passes with memtest, no errors. Any other ideas what I can check?

---

### Post by mörgæs on 2014-12-05
Did you try Ubuntu 14.10?

---

### Post by ughahaven on 2014-12-05
Just tried it, the live usb froze partway through login 3 times in a row, on the 4th it froze right after it loaded.
I then installed instead, and the full install process completed but then when I booted into the install, it stopped at a black screen (same thing when I tried to install linux mint).

The comp has two ram chips, I tried mint with one, still froze, then swapped them and tried it again. Still froze. So I'm pretty sure its not the memory.
I unplugged all cd/dvd drives and hard drives, booted it straight from the USB drive. Still froze.
I thought it might be the USB bus so I used USB->PS/2 adapters to plug in my keyboard and mouse, then tried a live CD of ubuntu 14.04. Still no luck.

Is it possible the power supply could be bad even with the power levels showing correct?

---

### Post by kccv42 on 2014-12-05
I noticed your computer only has 1 GB of ram. Try adding some more ram to your system. Even thoughh ubuntu can run with little ram, i have seen better performance(less freezing up) with 4GB of ram. Give it a try and let me know if it works.

---

### Post by ughahaven on 2014-12-05
I understand what you mean but I hesitate to buy memory for a system that may be completely unusable with linux. I'd like to try and figure out what the problem is first (as I'm pretty sure most flavors of linux can run with 1GB of ram).

I appreciate the advice though :)

---

### Post by mörgæs on 2014-12-05
1 GB of memory does not explain the freezing. Ubuntu will be slow but that's another matter. 

I don't have any good explanation for why only some distros freeze, though.

---

### Post by ughahaven on 2014-12-05
Update: Elementary installed doesn't work for some reason. Locks up at a black screen. Sometimes leaves a cursor on screen. Sometimes the cursor is usable for a few seconds then freezes.

Just to check, I reinstalled winXP and it works perfectly fine. No problems.

I'm kinda stumped to be honest. Not sure where to go from here to get linux working.

Odd thing happens though, when I've got bios up (was watching the health status for 10 minutes straight to check the power supply). If I plug in a flash drive while the bios setup is up, it freezes in bios.
Not otherwise though, left it sitting there a couple hours just to check. Its repeatable.

Is that just an odd thing? Or could that be a sign of what might be wrong?

I'm kinda just grasping at straws here :(

---

### Post by Darth Riker on 2014-12-05
Just a question - have you tried running a Live session (from USB or CD) of Lubutu or Xubuntu (selecting the right version of the distro for your machine of course)?

I would be interested to see if these crash on your system too (since they are Ubuntu at their core anyway).

---

### Post by ughahaven on 2014-12-06
I downloaded both the latest version of xubuntu and lubuntu based on your suggestions. I also formatted a 16GB flash drive I had laying around in case by some chance there's an error on the 4 GB. My results are:
Xubuntu live session worked perfectly. Install ran smoothly. I left it running a couple hours, during which a half hour with a youtube video running. Then I ran hardinfo's benchmarks. No problems so far.
Lubuntu live session worked perfectly. Install ran fine. I ran hardinfo benchmarks with no problem. Watched about 30 minutes of youtube videos then switched to another, then the mouse froze. Keyboard still worked. After a few minutes the whole system froze.
I then wanted to test mint and other distros again, this time ran off of my new flash drive. Result:
Mint Live USB session lasted long enough for me to install hardinfo, but froze before I could run it. Not a flash drive issue :(
Attempted Ubuntu 14.10 again, froze as soon as live session got to desktop.

Currently reinstalling Xubuntu for more testing.

Is there a better linux benchmarking software than hardinfo that I can use to tax/test the system and see if Xubuntu is stable enough to go with?

---

### Post by Darth Riker on 2014-12-07
Sounds like you're having an interesting time of things. :) I hope Xubuntu works out for you. That's the distro I'm going with as well for my old Dell Inspiron 8600.

I'm fairly new to linux (well ...I did use it a long time ago but long enough to now know nothing ..heh) but a quick google search in regards to benchmarking came up with these two results:

[http://www.howtogeek.com/111617/how-to-benchmark-your-linux-system-3-open-source-benchmarking-tools/](http://www.howtogeek.com/111617/how-to-benchmark-your-linux-system-3-open-source-benchmarking-tools/)

[http://www.linuxlinks.com/article/2012042806090428/BenchmarkTools.html](http://www.linuxlinks.com/article/2012042806090428/BenchmarkTools.html)

---

### Post by ughahaven on 2014-12-07
Welp, so far Xubuntu's doing decently.
I tried another few distros, Lxle, Q4OS, another version of bodhi. Some froze, some didn't.
It seems like there's something with Ubuntu based OSes that Xubuntu doesn't have, or something.
Isn't Unity based on gnome 2? I have no idea.

I'm happy at least that I can run Xubuntu instead of having to reinstall windows.

Thank you everyone who offered advice and support :) That's one thing that's amazing about linux, its community. You just can't beat it :)

---

### Post by mörgæs on 2014-12-07
Good :-) please keep us posted if you find the reason why only some distros are stable.

---

