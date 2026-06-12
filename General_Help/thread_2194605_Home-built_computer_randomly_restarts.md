---
title: "Home-built computer randomly restarts"
date: 2013-12-19
forum: General Help
---

### Post by joker0205 on 2013-12-19
Hello, I don't know if this is the right forum but I hope some of you can help me!

About two weeks ago I built my first computer, wiped and old harddrive and installed windows for gaming and ubuntu for everything else. All has been going fine (except ubuntu didn't boot properly after I activated the lastest nvidia drivers, but just deactivated them and it was back to normal) until yesterday, when, while waiting for a game of dota to start, my computer just restarted, no bluescreen or anything. This was on windows. I tried getting back into the game but in the loading screen it restarted again. After my third attempt I gave up. Tried with a different, non-steam game and when the game was loading my PC shut off. Came into ubuntu, installed steam to see if it was a windows problem and while it was downloading dota it shut off again. I suspect it might be a hardware problem, but since it has been working perfectly for the past 2 weeks I'm hesitant to blame it on that. Here's what appears when I write "sudo lshw" in the terminal:

```
description: Desktop Computer
    product: Z87X-D3H (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=To be filled by O.E.M. frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To be filled by O.E.M. uuid=9402DE03-8004-6605-D106-D80700080009
  *-core
       description: Motherboard
       product: Z87X-D3H-CF
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F3
          date: 04/16/2013
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cache:0
          description: L1 cache
          physical id: 4
          slot: CPU Internal L1
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-back
     *-cache:1
          description: L2 cache
          physical id: 5
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-back unified
     *-cache:2
          description: L3 cache
          physical id: 6
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CML8GX3M2A1600C9
             vendor: AMI
             physical id: 2
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CML8GX3M2A1600C9
             vendor: AMI
             physical id: 3
             serial: 00000000
             slot: ChannelB-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 41
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz
          slot: SOCKET 0
          size: 2700MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=4 enabledcores=1
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
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
             resources: irq:40 ioport:e000(size=4096) memory:d0000000-db0fffff
           *-display
                description: VGA compatible controller
                product: GK104 [GeForce GTX 770]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:da000000-daffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:db000000-db07ffff
           *-multimedia
                description: Audio device
                product: GK104 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:db080000-db083fff
        *-display
             description: VGA compatible controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:db400000-db7fffff memory:c0000000-cfffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:db834000-db837fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:db820000-db82ffff
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
             configuration: driver=mei latency=0
             resources: irq:44 memory:db83f000-db83f00f
        *-network
             description: Ethernet interface
             product: Ethernet Connection I217-V
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: 94:de:80:66:d1:d8
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=0.13-4 ip=192.168.1.96 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:42 memory:db800000-db81ffff memory:db83d000-db83dfff ioport:f080(size=32)
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:db83c000-db83c3ff
        *-multimedia:1
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:db830000-db833fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: 82801 PCI Bridge
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:db83b000-db83b3ff
        *-isa
             description: ISA bridge
             product: Z87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
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
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:db83a000-db83a7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:db839000-db8390ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EARS-00Y
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 80.0
             serial: WD-WCAV56176051
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=be6c03a1-e2d2-4068-8da1-956cc43a4205
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 1cee-026e
                size: 95MiB
                capacity: 99MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:1
                description: Windows reserved partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                serial: 6689aac4-32e1-4737-929d-6c9d8d2fb4de
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: f2780f43-3dd5-2e4c-8f9c-8d5797d01c80
                size: 834GiB
                capacity: 834GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2013-11-30 20:32:41 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: Linux swap volume
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 1
                serial: 171dd7b5-e81d-4c2c-a4f4-378ec8296a51
                size: 7811MiB
                capacity: 7812MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                logical name: /
                version: 1.0
                serial: 6215eeb6-7c4e-490f-9146-dbca3bf5a43d
                size: 89GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-12-01 18:56:14 filesystem=ext4 lastmountpoint=/ modified=2013-12-19 18:25:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-12-19 19:30:28 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD RW AD-5240S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.03
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh


```


If there's some better way of showing my sys specs I'd gladly do that!

Thanks alot in advance!

---

### Post by oldfred on 2013-12-19
Random shutdowns are very hard to debug.

Have you checked temperatures of cpu? Fans working correctly, used high quality silver paste, not very thick?
Often video drivers help control heat also. What video card and then what video driver?
Memory issues, checked memory with grub menu test. 

       sudo lshw | grep -A 11 display

---

### Post by joker0205 on 2013-12-19
Thanks for replying! Checked my CPU temperatures in BIOS right after one of the shutdowns, they were at 37 degrees C, the fans are working as they should, I've got 3 case fans and for the CPU the Coolermaster Evo 212, so I suppose the paste should be good.. Applied a little more than the size of a grain of rice, so I think there's no problem there. My video card is the Nvidia Geforce GTX770 with factory OC, and since there were problems with the drivers I have purged the nvidia drivers and reinstalled, but I deactivated that version (the 304) because I think it caused problems with booting. I'm going to check my memory after posting this, and as for the command this is what appears: 

```
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GK104 [GeForce GTX 770]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:da000000-daffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:db000000-db07ffff
--
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller cap_list
             configuration: latency=0
             resources: memory:db400000-db7fffff memory:c0000000-cfffffff ioport:f000(size=64) 

```


Edit: Just tried to run memtest from grub2, but got the message "Error: Unknown command 'linux16'". Also tried installing some new video drivers but the system wouldn't boot normally so I had to enter low-grafics mode and purge the nvidia files.. Now looks normal again.

---

### Post by Easy Limits on 2013-12-19
Since you only have two sticks of RAM make sure they are in the same colored slots on the motherboard.  Next, I would run Memtest followed by a CPU temp check, which it sounds like you already have.  

Are your fans controlled by the motherboard or an external device?

---

### Post by oldfred on 2013-12-19
The Haswell processors are supposed to consume even less power and have good video on there own. 

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

      
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

Does the motherboard then support dual video?

 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by joker0205 on 2013-12-20
I made sure that the sticks are correctly placed. The case fans are connected with 3-pins to the power supply, the CPU-one to the motherboard! As I wrote in my edit of my last post I have problems running memtest, seems to be a problem with me having EFI... Haven't found any solution to that online yet.

---

### Post by joker0205 on 2013-12-20
Oldfred: I'm going to check those things out as soon as I get home!

---

### Post by mörgæs on 2013-12-20
Which versions of Buntu have you tried?

---

### Post by oldfred on 2013-12-20
I do now remember that memory test that grub calls uses Linux16, which is a different mode & UEFI has to say in the same mode.

---

### Post by joker0205 on 2013-12-20
> **mörgæs said:**
> Which versions of Buntu have you tried?

Only 12.04 LTS so far!

---

### Post by joker0205 on 2013-12-20
> **oldfred said:**
> The Haswell processors are supposed to consume even less power and have good video on there own. 

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

      
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

Does the motherboard then support dual video?

 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

I'm not entierly sure what you want me to do.. Should I update my version of Ubuntu to Saucy Salamander for the drivers to work? And could this help me with my shut-down problem?

---

### Post by mörgæs on 2013-12-20
Then my first advise would be trying 13.10 in a fresh install for comparison. When dealing with 'difficult' problems it's important with more data points.

---

### Post by oldfred on 2013-12-20
+1 on another install of 13.10

If you have 10 to 25GB on hard drive you can just install to a new partition and use it for test. I actually have lots of installs just to try things and I had space on hard drive and have not deleted many which should be since they now are obsolete.

---

### Post by daniell59 on 2013-12-20
Check to see that the voltage to the memory is correct. On my present MB, I had to manually set the voltage in the BIOS. The default setting was wrong. Also check the timing.

---

### Post by joker0205 on 2013-12-20
I just installed ubuntu 13.10, fixing the GRUB now so I can enter windows too! I'm going to check the voltage too, but other than that, what do I do?

---

### Post by joker0205 on 2013-12-20
Did I just overwrite my windows...? When installing, I had the alternative of erasing previous version of ubuntu and do a "clean install", thought it would only affect the partition I had made for Ubuntu... This is what I get after running Boot Repair: [http://paste.ubuntu.com/6607858/](http://paste.ubuntu.com/6607858/) Please tell me it doesn't mean what I think it means.... Is there any way to recover anything?

---

### Post by oldfred on 2013-12-20
It looks like your Windows is gone. And since at least parts would be overwritten you cannot recover a bootable configuration.
You may be able to recovery parts or some of your files since an Ubuntu install is not large.

I would try testdisk first and see if deeper search finds files. That may be the only way to get files with full names.
Then photorec or Windows apps that are drive scanners can scan a drive for anything that looks like a file by type. It only finds extension, is very slow, also finds deleted files so a lot of space to copy to is required. 

Sounds similar to this bug, not sure if others closer. Best to add to bug report or it will not be reviewed with just one report.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1225534](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1225534)

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

      
 For NTFS, but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)


 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

This is the screen I get & it clearly says everything will be overwritten. But I always use Something Else just in case.

---

### Post by joker0205 on 2013-12-20
Booted from USB and got photorec started, only 10h of waiting now.. Is it possible to run both photorec and testdisk at the same time? Btw, when I installed I saw this: [http://i.stack.imgur.com/rJuy0.png](http://i.stack.imgur.com/rJuy0.png) so no alarm bell rang in my head :(

---

### Post by oldfred on 2013-12-20
Pretty sure you cannot run testdisk and photorec at same time unless you copied an image of drive to another system.

Your image looks like it just had one copy of Ubuntu 11.10 and no other systems. Because I have multiple systems and want to be sure of where it installs I always use manual install or Something else. But that is not even a guarantee. I have many partitions on sdc and have chosen the wrong one. (possibly the old in oldfred :) )

---

### Post by joker0205 on 2013-12-21
Ok, so I just used testdisk to try to recover my files, got to this after doing a deeper search:[ATTACH=CONFIG]248786[/ATTACH] after pressing "P" it didn't show my files, and it seems as if the terminal started responding to what I do instead of testdisk, and after waiting for 7 hours I really don't want everything go to waste, so is there any way of getting back to testdisk without having to restart everything? :(

---

### Post by oldfred on 2013-12-21
Are you in the correct place? You did not have MAC HFS partitions did you? 
One of the first choices is whether drive is MBR or gpt and that needs to be correct for it to try to figure out drive.

---

### Post by PJs Ronin on 2013-12-22
Has this topic drifted from the OP?   Has the shutdown problem been rectified?

In my experience about the only thing that causes immediate computer shutdowns is thermal overload.   That doesn't necessarily mean that the CPU is cooking... it may be a case that the threshold has been (inadvertently) lowered and simply triggered a scram.

Or have I missed something here.

---

