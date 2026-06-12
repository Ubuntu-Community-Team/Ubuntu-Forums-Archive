---
title: "Mouse cursor is stuck"
date: 2014-11-02
forum: General Help
---

### Post by guiliker on 2014-11-02
For the past few weeks my mouse cursor suddenly becomes imprisoned. By this I mean I am using one of my mice (Microsoft Basic Optical USB or Logitech Wireless USB) and the cursor becomes stuck. I can still move my mouse around the screen and click - I just can't tell where I am clicking, as the cursor does not move. If the open window has hyperlinks on it and they scroll past the imprisoned cursor then cursor icon changes to the finger. Also the mouse scroll and autoscroll functions still work. I don't really use keyboard shortcuts, as I never remember them, so I creep around the screen until I manage to click the icon for the logout/shutdown session menu. When I click on Logout it just hangs, however selecting reboot or shutdown resolves the problem. 

This has happened at a variety of times: initial start-up before opening any documents/apps; with just 1 document open in LibreOffice Writer; with Chromium running mid-email; with Gramps and Chromium running; with Firefox, KMag, and OnBoard running; and with Brightness v.2 (from GitHub) and LibreOffice Writer.

I have Lubuntu 14.04 which was upgraded from 13.10.

Let me know what else to provide to help you to help me.

Thanks in advance :)

```
computer
    description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-07-07 12:12+0000X-Generator: Launchpad (build 17086)
    product: * ()
    vendor: MAXDATA
    version: 5123660003
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: DQ965CO
       vendor: Intel Corporation
       physical id: 0
       version: AAD46480-501
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.6
          serial: [REMOVED]
          slot: LGA 775
          size: 1862MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 2MiB
             capacity: 2MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
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
     *-cache
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 4
          version: MQ96510J.54T.0013.2006.1009.1701
          date: 10/09/2006
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 0x000000000000000000000000000000000000
             vendor: 0x0000000000000000
             physical id: 0
             serial: [REMOVED]
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: [REMOVED]
             slot: J6H2
        *-bank:2
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 2
             serial: [REMOVED]
             slot: J6J1
        *-bank:3
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: [REMOVED]
             slot: J6J2
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:50200000-502fffff memory:40000000-4fffffff ioport:2140(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:50100000-501fffff
        *-communication
             description: Communication controller
             product: 82Q963/Q965 HECI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:46 memory:50325900-5032590f
        *-network
             description: Ethernet interface
             product: 82566DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.1-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:45 memory:50300000-5031ffff memory:50324000-50324fff ioport:20c0(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:20a0(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:2080(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:50325400-503257ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:50320000-50323fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:50400000-504fffff ioport:50800000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:50000000-500fffff ioport:50a00000(size=2097152)
           *-ide
                description: IDE interface
                product: 88SE6101/6102 single-port PATA133 interface
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list
                configuration: driver=pata_marvell latency=0
                resources: irq:17 ioport:1018(size=8) ioport:1024(size=4) ioport:1010(size=8) ioport:1020(size=4) ioport:1000(size=16) memory:50000000-500001ff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:50500000-505fffff ioport:50c00000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:50600000-506fffff ioport:50e00000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:6000(size=4096) memory:50700000-507fffff ioport:51000000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:2060(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:2040(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:2020(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:50325000-503253ff
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:2138(size=8) ioport:2154(size=4) ioport:2130(size=8) ioport:2150(size=4) ioport:2110(size=16) ioport:2100(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:50325800-503258ff ioport:2000(size=32)
        *-ide:1
             description: IDE interface
             product: 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:2128(size=8) ioport:214c(size=4) ioport:2120(size=8) ioport:2148(size=4) ioport:20f0(size=16) ioport:20e0(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HDT722516DLA380
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: V43O
             serial: [REMOVED]
             size: 153GiB (164GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0005ac91
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 29GiB
                capacity: 29GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-06-23 18:06:25 filesystem=ntfs state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 123GiB
                capacity: 123GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: W95 FAT32 partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 68GiB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 2860MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 52GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW SH-S182D
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SB02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.13.0-39-generic firmware=N/A ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by bapoumba on 2014-11-02
Hello,

I have a different issue with the mouse cursor, but I noticed you have an Intel video card, so have I. I had found this a while back that could at least describe what you are experimenting :
[http://forum.lxde.org/viewtopic.php?f=3&t=31149](http://forum.lxde.org/viewtopic.php?f=3&t=31149)
[http://forums.debian.net/viewtopic.php?f=6&t=61447&start=15](http://forums.debian.net/viewtopic.php?f=6&t=61447&start=15)

It does come back to normal for me waking up from sleep or suspend (as described in the two old threads). Does it automagically come back after waking up from sleep for you ? I have not investigated further.

---

### Post by vasa1 on 2014-11-02
> **guiliker said:**
> For the past few weeks my mouse cursor suddenly becomes imprisoned ... 
...
with just 1 document open in LibreOffice Writer; with Chromium running mid-email; with Gramps and Chromium running; with Firefox, KMag, and OnBoard running; and with Brightness v.2 (from GitHub) and LibreOffice Writer.

I have Lubuntu 14.04 which was upgraded from 13.10.
...
Can you correlate when this problem started with any software installed at the time?

---

### Post by guiliker on 2014-11-02
Thank you for your post bapoumba, however I am not experiencing anything like those described in those links. I cannot tell you the effect of suspend is on the problem as suspend does not work for me - it just hangs. I don't use suspend so have never seen it as a problem that needs fixing.

Thank you for you response Vasa1. I have not installed anything for quite some months - I  have only been doing the updates when the appear. I do not know where to look for an update log. Therefore, I do not know which software to start looking at. I have look through the various logs for warning and error messages and all I have been able to find is below and is seemingly unrelated 
```
Nov  2 05:18:31 guiliker kernel: [ 4762.000031] [drm] stuck on render ring
Nov  2 05:18:31 guiliker kernel: [ 4762.000039] [drm] GPU crash dump saved to /sys/class/drm/card0/error
Nov  2 05:18:31 guiliker kernel: [ 4762.000042] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
Nov  2 05:18:31 guiliker kernel: [ 4762.000044] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
Nov  2 05:18:31 guiliker kernel: [ 4762.000046] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
Nov  2 05:18:31 guiliker kernel: [ 4762.000048] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
Nov  2 05:18:31 guiliker kernel: [ 4762.000991] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0xf18a000 ctx 0) at 0xf18af84
Nov  2 05:18:32 guiliker kernel: [ 4762.268024] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
Nov  2 05:18:32 guiliker kernel: [ 4762.508026] [drm:i915_reset] *ERROR* Failed to reset chip. 
```

---

### Post by guiliker on 2014-11-03
Worryingly this could be something more sinister?! It has just happened again and instead of creeping around the desktop until I eventually get to the shutdown menu icon, I decided to try saving the document I was working on and resetting the sliders on the brightness app (detailed in my earlier post). The save said it worked, but on trying to reset the sliders there was no change to the colour or brightness of my screen. In a panic I go for shutdown. On restart the mouse was working correctly and my screen brightness/colour had reset itself. However the saved document didn't exist. I'm now worrying that this could be something "more" than just something buggy in the mouse software?!? :-s

---

### Post by bapoumba on 2014-11-03
I may be wrong, but the file not being saved could be due to the force shutdown rather than something else. Did you save it to the drive or somewhere else ?

---

### Post by guiliker on 2014-11-04
Hello bapoumba, the file was saved to my home folder. Forgive my confusion, I may be misunderstanding, but I thought that the shutdown would be the same as any 'normal' shutdown as I'm not pressing any power buttons or running any special script just selecting the shutdown option on the shutdown menu?!?

---

### Post by guiliker on 2014-11-04
Well guess what it has just happened again and this time I went straight to the logs and I found that the quote from the kern log in post #4 was there! Googling I found: [https://www.libreoffice.org/bugzilla/show_bug.cgi?id=77207](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=77207) , but I am not sure what it means and incidentally the file at /sys/class/drm/card0/error just says 'no error state collected'. I'm wondering if any of the packages mentioned in the bugzilla link is related to my issues :s

---

### Post by bapoumba on 2014-11-05
Sorry I have not answered. I will have a look :)

---

### Post by guiliker on 2014-11-12
Hey,

It's just done it again. I just ran software update and chromium was updated and now if I open chromium on any page with any flash my mouse gets stuck and chromium announces there is a fault and tries to close. The following has been added after the previous excerpt in the kern log:
```
Nov 13 02:21:43 guiliker kernel: [  573.871456] chromium-browse[2593]: segfault at bf56efec ip b1f6e4e5 sp bf56eff0 error 6 in libblink_web.so[b0f03000+1bd9000]
Nov 13 02:21:53 guiliker kernel: [  583.960276] perf samples too long (2595 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Nov 13 02:22:05 guiliker kernel: [  595.718712] Watchdog[2482]: segfault at 0 ip b01a2ac7 sp ad250be0 error 6 in libcontent.so[af9d8000+1180000]
Nov 13 02:22:13 guiliker kernel: [  604.000014] [drm] stuck on render ring
Nov 13 02:22:13 guiliker kernel: [  604.000021] [drm] GPU crash dump saved to /sys/class/drm/card0/error
Nov 13 02:22:13 guiliker kernel: [  604.000023] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
Nov 13 02:22:13 guiliker kernel: [  604.000025] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
Nov 13 02:22:13 guiliker kernel: [  604.000027] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
Nov 13 02:22:13 guiliker kernel: [  604.000029] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
Nov 13 02:22:13 guiliker kernel: [  604.000909] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0x5180000 ctx 0) at 0x5180b88
Nov 13 02:22:13 guiliker kernel: [  604.072025] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
Nov 13 02:22:14 guiliker kernel: [  604.512014] [drm:i915_reset] *ERROR* Failed to reset chip.
```

---

### Post by guiliker on 2014-11-12
The OP in this thread has a better description of what I have been experiencing: [http://ubuntuforums.org/showthread.php?t=2252092&page=2&p=13166214#post13166214](http://ubuntuforums.org/showthread.php?t=2252092&page=2&p=13166214#post13166214)

---

### Post by bapoumba on 2014-11-13
I hope that you'll get an answer because I'm a little bit at loss here.. Lokked around the other day and did not find anything relevant.

---

### Post by mrsthursday on 2014-11-18
I started using Lubuntu abt a year ago but my troubles with the mouse only started when out of the blue sometime ago I started receiving regular updates from Lubuntu. 

Plus I now have trouble with my PC freezing where it never did this before.

---

### Post by vasa1 on 2014-11-18
> **mrsthursday said:**
> I started using Lubuntu abt a year ago but my troubles with the mouse only started when out of the blue sometime ago I started receiving regular updates from Lubuntu. 

Plus I now have trouble with my PC freezing where it never did this before.Please start a new thread with details of *your* situation: information such as your Lubuntu version and your computer specs may help.

---

### Post by guiliker on 2014-11-20
Just to say that I have still not been able to solve my issue however I can now say that it also effects other *buntu flavours such as ubuntu, xubuntu and gubuntu. It has also happened in relation to certain sigsegv segmentation faults with the following applications Google Chrome, LXPanel, Gramps, and Firefox as well as occurring in relation to either html5 or flash video. I have however not been able to replicate these with success. This could be because these applications have recently been updated. I have read that this issue could be in relation to bad memory or memory overuse, however using a htop log shows that the memory has not been maxed out when these events occur and memtest on being run for about 60-odd hours didn't report a problem. I cannot run 14.10 to check if it is a problem there as I only have 1gb RAM so I worry it may kill my PC!

---

### Post by bapoumba on 2014-11-23
Hmm. Maybe if you start these apps from a terminal, you'll get some error to work with.

---

