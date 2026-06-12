---
title: "Random Freezing (in 14.04.5 LTS)"
date: 2016-08-27
forum: General Help
---

### Post by Lightning Dragon on 2016-08-27
Hello,

I am on Ubuntu 14.04.5, fresh install (update did not go so well). I have had one consistent problem since installing and that is frequent but random freezing. I am able to still move my mouse around and I can click things, but my keyboard doesn't seem to recognize when keys are pressed. If I do "ctrl+alt+delete" to bring up an overlay to log out or lock the computer, this will stop the mouse from being able to click things but still be able to move around the screen. Also, if I have music playing it will still play through the lockup/freeze, even in TTY1.

The only way out of the freeze is a hard reboot or if I use ctrl+alt+f1, log in and do "pkill -9 compiz". I have noticed that the freezes will happen far more frequently if I use more than one application with Firefox. I am just about to test the computer by just running Firefox but as you can imagine this is getting pretty annoying. I have lost a lot of work due to the freezes. Is this a problem with 14.04.5 or compiz?

 Thanks for any help! :)

---

### Post by Topsiho on 2016-08-27
Hi,

I had the same problem, or such a problem, after install, first of 16.04, and then of 14.04.3, on one of my computers. Sudden and random freezes, not very frequent but still as if I were using Windows. Checked my hardware as far as I was able to, and my suspicion was, with luck it was the graphics card. Changed the nouveau driver for a driver from the graphics card manufacturer (nouveau for nvidia binary driver 340.96), and this seems to have solved the problem. I tested it on 14.04, and I am now testing it on 16.04. On 16.04 the testing just started an hour ago, but that on 14.04 I tested it for 3 days without freezes. I write this on 16.04, foolhardy fellow that I am :)

Hope this helps,

Topsiho

---

### Post by mörgæs on 2016-08-28
Is there any Nvidia present at all? Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Lightning Dragon on 2016-08-28
Hello,

@Topsiho

I will try installing the drivers from the AMD website then, thank you! I hope it works! *fingers crossed*

@mörgæs

This is a fresh install, so no drivers have yet to be installed. I'm using a AMD card by the way (sorry for not mentioning that earlier). Here is the result of the code regardless:

```

computer
    description: Desktop Computer
    product: MS-7821 (To be filled by O.E.M.)
    vendor: MSI
    version: 2.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=To be filled by O.E.M. frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To be filled by O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Z87-G45 (MS-7821)
       vendor: MSI
       physical id: 0
       version: 2.0
       serial: [REMOVED]
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V10.7
          date: 07/19/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 3d
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz
          slot: SOCKET 0
          size: 3389MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm arat pln pts cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L2 cache
             physical id: 3e
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3f
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back
        *-cache:2
             description: L3 cache
             physical id: 40
             slot: CPU Internal L3
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: CMZ8GX3M2A1600C9
             vendor: AMI
             physical id: 1
             serial: [REMOVED]
             slot: ChannelA-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: CMZ8GX3M2A1600C9
             vendor: AMI
             physical id: 3
             serial: [REMOVED]
             slot: ChannelB-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:f7e00000-f7efffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:31 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff
           *-multimedia
                description: Audio device
                product: Tahiti XT HDMI Audio [Radeon HD 7970 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:30 memory:f7e60000-f7e63fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:25 memory:f7f00000-f7f0ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:28 memory:f7f1a000-f7f1a00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7f18000-f7f183ff
        *-multimedia
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:f7f10000-f7f13fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:d000(size=4096) memory:f7d00000-f7dfffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:27 ioport:d000(size=256) memory:f7d00000-f7d00fff memory:f0000000-f0003fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7f17000-f7f173ff
        *-isa
             description: ISA bridge
             product: Z87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7f16000-f7f167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7f15000-f7f150ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1D05
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=83fc1c28
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 98MiB
                capacity: 100MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2015-08-04 06:44:19 filesystem=ntfs state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2015-08-04 06:44:12 filesystem=ntfs label=Windows7 modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKS-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 1D05
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0000c238
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 457GiB
                capacity: 457GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-08-23 01:36:00 filesystem=ext4 lastmountpoint=/ modified=2016-08-27 02:22:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-08-27 02:22:01 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                size: 8135MiB
                capacity: 8135MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 8135MiB
                   capabilities: nofs
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AADS-1
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 0A80
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=ecd07c0e
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                version: 3.1
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2016-05-27 05:24:43 filesystem=ntfs label=Games 2 state=clean
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh

```

---

### Post by Topsiho on 2016-08-28
Hello Lightning Dragon,

No need to go to AMD (?) website. Just start Extra Hardware, and choose the other driver ...
That's all.

My computer still runs as hoped for :)

Topsiho

---

### Post by Lightning Dragon on 2016-08-28
> **Topsiho said:**
> Hello Lightning Dragon,

No need to go to AMD (?) website. Just start Extra Hardware, and choose the other driver ...
That's all.

My computer still runs as hoped for :)

Topsiho

Hello,

I never got those to work for me before, so I normally install manually, which is no problem. However that doesn't seem to work any more. If I use the drivers in Additional Hardware, which do I use? There are two options after the default one.

---

### Post by Topsiho on 2016-08-28
I think you mean Extra Hardware, or else we are talking on different lines.

I don't know about the options you get. I would try the different options until you get the right one.
Sometimes the extra information gives you a clue which is the best one.
I only have trouble using an Nvidia card in one of my computers, the other computers run perfectly with the open source driver, nouveau.

So if you experience the problems you describe, I assume you have an Nvidia card.

My (Nvidia) computer runs perfectly, thus far, on both 16.04 and 14.04, with the Nvidia binary driver.

Succes,

Topsiho

---

### Post by Topsiho on 2016-08-28
I just saw you have an AMD Radeon processor:

*-display
                description: VGA compatible controller
                product: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]

So probably my information is useless, sorry for that.

Still, you might try another driver. My computer with a Radeon graphics card runs perfectly with nouveau.

Topsiho

---

### Post by mörgæs on 2016-08-28
> **Topsiho said:**
> My computer with a Radeon graphics card runs perfectly with nouveau.


It will also run perfectly without. Nouveau is a driver for Nvidia graphics processors and has no relevance for Radeon.

---

### Post by Lightning Dragon on 2016-08-29
Well, neither of them stopped the freezing problem. I noticed a decrease in performance too (everything would be super slow opening up), so I had to revert back to the default option. :(

---

### Post by mörgæs on 2016-08-29
How does it work in a live boot of 16.04.1?

---

### Post by ventrical on 2016-08-29
> **Lightning Dragon said:**
> Well, neither of them stopped the freezing problem. I noticed a decrease in performance too (everything would be super slow opening up), so I had to revert back to the default option. :(

Most ATI graphics cards are no longer supported (diligently)  . In 16.04 you will get llvmpipe. If you have HWE stack from trusty upgrade (xenial) you most likely have llvmpipe running which can render some machines to molasses. You can try fresh install (trusty) with nomodeset. It will work with some and not on others.

Regards..

---

### Post by Lightning Dragon on 2016-08-29
Hello,

> **mörgæs said:**
> How does it work in a live boot of 16.04.1?

I will download and test it, however when I tested 16.04 and 14.04 Trusty again I never experienced the freezing, just other minor issues.

@ventrical

May I ask how I can check if my card is not supported any more? It isn't a very old card at all. Oh, and I tried a fresh install of 14.04 Trusty before I reinstalled 14.04.5 (due to the upgrade it wanted) and I didn't experience the problems.

---

### Post by Topsiho on 2016-08-29
I am now running the computer with the Radeon videocard, and looked for the 
Extra Hardware, but it didn't suggest other graphics drivers. The two options given are quite something else.
It's quite true that this computer runs perfectly without nouveau :o. My mistake. Thank you mörgæs.

Topsiho

---

### Post by mörgæs on 2016-08-30
> **Lightning Dragon said:**
> 
May I ask how I can check if my card is not supported any more? 

It is definitely supported but not with closed-source drivers. AMD is moving towards open source drivers, which are the only ones available in 16.04. 

The only question is whether the new drivers have caught up already. If you have some space left you could do a dual boot (14.04.5 and 16.04.1) for comparison.

---

### Post by Lightning Dragon on 2016-08-31
> **mörgæs said:**
> It is definitely supported but not with closed-source drivers. AMD is moving towards open source drivers, which are the only ones available in 16.04. 

The only question is whether the new drivers have caught up already. If you have some space left you could do a dual boot (14.04.5 and 16.04.1) for comparison.

In comparison to 14.04.5 and 16.04.1 concerning bugs/stability, the better for me is 14.04.5 since I am only facing the one freezing issue. I tested the drivers on 16.04.1 when I installed it though and I didn't see any problems with it. I didn't try gaming on it of course but it worked just fine.

---

### Post by mörgæs on 2016-09-01
> **Lightning Dragon said:**
> In comparison to 14.04.5 and 16.04.1 concerning bugs/stability, the better for me is 14.04.5 since I am only facing the one freezing issue.

Why? If I read your post correctly then you have met problems in 14.04 but none in 16.04.1.

---

### Post by Lightning Dragon on 2016-09-01
> **mörgæs said:**
> Why? If I read your post correctly then you have met problems in 14.04 but none in 16.04.1.

I only have one issue in 14.04.5, which is the random freezing when using browsers or multiple applications, but in 16.04.1 I have far more issues, such as graphical issues (pixelized screens and log ins), performance drops, unity problems (crashes constantly) and specific software problems.

---

### Post by kansasnoob on 2016-09-01
I've also had nothing but trouble with 16.04 (Xenial), and even Trusty installed using the 14.04.5 media is troublesome since it uses the Xenial HWE stack, so I've just been installing using [the archived 14.04.1 media]("http://old-releases.ubuntu.com/releases/trusty/") which uses the 3.13 series kernel and matching X-stack which is supported until April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

There was however a nasty installer bug in 14.04.1 that can wipe everything out in dual-boots so you must use the Something else (advanced  partitioning) option to avoid that:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Note: Trusty images newer than 14.04.1 have the HWE stacks so you must use 14.04.1 media to avoid HWE!

---

### Post by Lightning Dragon on 2016-09-05
> **kansasnoob said:**
> I've also had nothing but trouble with 16.04 (Xenial), and even Trusty installed using the 14.04.5 media is troublesome since it uses the Xenial HWE stack, so I've just been installing using [the archived 14.04.1 media]("http://old-releases.ubuntu.com/releases/trusty/") which uses the 3.13 series kernel and matching X-stack which is supported until April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

There was however a nasty installer bug in 14.04.1 that can wipe everything out in dual-boots so you must use the Something else (advanced  partitioning) option to avoid that:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Note: Trusty images newer than 14.04.1 have the HWE stacks so you must use 14.04.1 media to avoid HWE!

I heard about the bug, so I had to go with the latest 14.04.5. I couldn't locate the older images and only had one DVD to burn with. I guess I'm stuck with 14.04.5's freezing for a while. Maybe a future update will fix it somehow. :(

---

