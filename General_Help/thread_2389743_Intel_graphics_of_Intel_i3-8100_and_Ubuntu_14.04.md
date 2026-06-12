---
title: "Intel graphics of Intel i3-8100 and Ubuntu 14.04"
date: 2018-04-21
forum: General Help
---

### Post by mtro2 on 2018-04-21
Guys, help please, I've got new PC for work with next configuration:

System Information

Hardware:
```
Processor: Intel Core i3-8100 @ 3.60GHz (4 Cores), 
Motherboard: Gigabyte B360M DS3H, 
Chipset: Intel Device a36f, 
Memory: 16384MB, Disk: 275GB Crucial_CT275MX3, 
Graphics: Intel Device 3e91, 
Audio: Realtek ALC887-VD, 
Network: Realtek RTL8111/8168/8411
```

Software:
```
OS: Ubuntu 14.04, 
Kernel: 3.13.0-144-generic (x86_64), 
Desktop: Unity 7.2.6, Display Server: X Server 1.15.1, 
Display Driver: intel 2.99.910, 
Compiler: GCC 4.8, 
File-System: ext4,
 Screen Resolution: 1024x768
```

But I have problem with intel graphic driver for my pc: only one resolution 1024x768,  no setted driver for VGA compatible controller, and monitors are not detected correctly (after rebooting system two both VGA and HDMI work like mirrors).
I have found thread [https://ubuntuforums.org/showthread.php?t=2377324](https://ubuntuforums.org/showthread.php?t=2377324), but this resolving doesn't work in ubuntu 14.04. 
Does anyone know what can help me? :) 

Maybe you had same problem in 14.04 or I should reinstall system and try 17.10?

sudo lshw -c video

```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:4000(size=64)
```

lspci -k

```
00:00.0 Host bridge: Intel Corporation Device 3e1f (rev 08)
    Subsystem: Gigabyte Technology Co., Ltd Device 5000
00:02.0 VGA compatible controller: Intel Corporation Device 3e91
    Subsystem: Gigabyte Technology Co., Ltd Device d000
00:12.0 Signal processing controller: Intel Corporation Device a379 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 8888
00:14.0 USB controller: Intel Corporation Device a36d (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 5007
    Kernel driver in use: xhci_hcd
00:14.2 RAM memory: Intel Corporation Device a36f (rev 10)
    Subsystem: Intel Corporation Device 7270
00:16.0 Communication controller: Intel Corporation Device a360 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 1c3a
00:17.0 SATA controller: Intel Corporation Device a352 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device b005
    Kernel driver in use: ahci
00:1d.0 PCI bridge: Intel Corporation Device a330 (rev f0)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge: Intel Corporation Device a308 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 5001
00:1f.3 Audio device: Intel Corporation Device a348 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device a182
    Kernel driver in use: snd_hda_intel
00:1f.4 SMBus: Intel Corporation Device a323 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 5001
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device a324 (rev 10)
    Subsystem: Intel Corporation Device 7270
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 16)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard
    Kernel driver in use: r8169
```

dmesg | grep -i i915
```

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-144-generic.efi.signed root=UUID=07e8053c-8a36-4654-ac5a-a2e864fdd488 ro quiet splash i915.alpha_support=1 vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-144-generic.efi.signed root=UUID=07e8053c-8a36-4654-ac5a-a2e864fdd488 ro quiet splash i915.alpha_support=1 vt.handoff=7
[    5.691051] i915: unknown parameter 'alpha_support' ignored
```

---

### Post by deadflowr on 2018-04-21
Try the upgraded hardware stack:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr")

the X11 and kernel stacks you have are the older original stacks for 14.04.
While still supported, those are better served for older hardware.
For new hardware, you'll want to try the upgraded hwe stacks as described in the link.

And even then, you might be better off installing Ubuntu 16.04 and try it's upgraded hardware stack option, which is even newer than what you would get from 14.04;s upgrades hardware stack.

Hope it helps.

---

### Post by sudodus on 2018-04-21
Intel i3-8100 is 8th generation processor and built-in graphics, which is much newer than Ubuntu 14.04.

I suggest that you try 16.04.4 or Bionic (to be released as 18.04 LTS very soon). The newer versions of Ubuntu bring newer linux kernels and newer hardware drivers, that are more likely to work your graphics card. You are welcome to help test the developing version (and discuss it at the [Ubuntu Forum for the developing release](https://ubuntuforums.org/forumdisplay.php?f=427)).

---

### Post by mtro2 on 2018-04-21
Thank you very much, guys! I have installed Ubuntu 16.04 and intel drivers is being used now. Now I have problem with Unknown Monitor, but I think it's already another story :)

sudo lshw -c video
```

*-display               
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:425 memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:4000(size=64) memory:c0000-dffff

```

---

