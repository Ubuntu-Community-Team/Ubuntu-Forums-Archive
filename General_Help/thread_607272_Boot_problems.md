---
title: "Boot problems"
date: 2007-11-08
forum: General Help
---

### Post by Silenus on 2007-11-08
At boot I get kernel panic errors, this only happens when I have it set to boot with video from my ati radeon 9250 card, when I switch it to onboard intel graphics it works fine. But the problem is that I would like to use my ATI card, and have something other than basic vesa drivers, when I can be using a card that has a little more power.

This is the lspci of the system
```
george@debian:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
        Subsystem: Hewlett-Packard Company Unknown device 2a08
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 2a08
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at bfd00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at cc00 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at bfcc0000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82915G Express Chipset Family Graphics Controller (rev 04)
        Subsystem: Hewlett-Packard Company Unknown device 2a08
        Flags: bus master, fast devsel, latency 0
        Memory at bfd80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at c480 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at c800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at c880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 193
        Memory at bfcbbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: bfe00000-bfffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 201
        I/O ports at c080 [size=8]
        I/O ports at c000 [size=4]
        I/O ports at bc00 [size=8]
        I/O ports at b880 [size=4]
        I/O ports at b800 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: medium devsel, IRQ 201
        I/O ports at 0400 [size=32]

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a0b
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at e800 [size=256]
        Memory at bffffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 2002
        Flags: medium devsel, IRQ 11
        Memory at d0000000 (32-bit, prefetchable) [disabled] [size=128M]
        I/O ports at e000 [disabled] [size=256]
        Memory at bffd0000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Expansion ROM at bff00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:03.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
        Subsystem: ATI Technologies Inc Unknown device 2003
        Flags: bus master, medium devsel, latency 64
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at bffe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Flags: bus master, slow devsel, latency 64, IRQ 225
        Memory at bfffe000 (32-bit, non-prefetchable) [size=4K]
        Memory at bfe00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

george@debian:~$ 
```

The kernel panic error

[CODE<0> Kernel Panic - Not syncing: Fatal exception in interrupt
<1> BUG: Unable to handle kernel paging request at virtual address ffffd370 printing eip:
c0110ae2
*pde = 00004067
*pte = 1f116021
Ooops: 0003 [#38]
SMP
Modules linked in: Intel_agp agpgart evdev ext3 jbd mbcache sd_mod ide_cd cdrom ata_piix 9139too libdata usb_storage scsi_mod 8139cp mii generic piix ide_core elci_hcd uhci-hcd usbcore thermal processor fan
cpu: 0
EIP: 0060:[<c0110ae27>] Not tainted VLI
EFLAGS: 00010006 (2.6.18-5-686#1)
EIP is at clear_local_apic+0xc/0xt4
][/CODE]

when tried with nolapic

```
ATA: Abnotmal status 0xD8 on port 0XC087

ata1.00:failed to identify I/0 error, err mask = Ox4

8139 cp 0000:02:02.0: This (id loec:8139 rev 10) is not an 8139ct compatable chip try the "8139too" driver instead

Alert /dev/sda1 does not exist dropping to shell
```


Help is appreciated.

---

### Post by dcstar on 2007-11-08
> **Silenus said:**
> At boot I get kernel panic errors, this only happens when I have it set to boot with video from my ati radeon 9250 card, when I switch it to onboard intel graphics it works fine. But the problem is that I would like to use my ATI card, and have something other than basic vesa drivers, when I can be using a card that has a little more power.

This is the lspci of the system
```
george@debian:~$ lspci -v
..........
02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 2002
        Flags: medium devsel, IRQ 11
        Memory at d0000000 (32-bit, prefetchable) [disabled] [size=128M]
        I/O ports at e000 [disabled] [size=256]
        Memory at bffd0000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Expansion ROM at bff00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:03.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
        Subsystem: ATI Technologies Inc Unknown device 2003
        Flags: bus master, medium devsel, latency 64
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at bffe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
..........

george@debian:~$ 
```
........
Help is appreciated.

I don't really understand why there are two ATI cards listed there, and why the first one has so many "disabled" entries - I would guess this is the root cause of your problems.

What is in your xorg.conf file when it is configured for the ATI?

---

### Post by Silenus on 2007-11-09
I don't understand by what you mean with configured for ATI, when I first installed the system and had to go to onboard after installing with ati it had ati listed at the PCI slots, which I then moved to Intel to allow me to boot.

---

### Post by Silenus on 2007-11-09
Any other ideas?

---

### Post by Silenus on 2007-11-10
I've tried to change the config and it seems to provide no change.

---

