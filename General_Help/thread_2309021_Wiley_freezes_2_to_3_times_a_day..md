---
title: "Wiley freezes 2 to 3 times a day."
date: 2016-01-07
forum: General Help
---

### Post by anton.lauridsen on 2016-01-07
I recently installed wiley in a dual boot setup. Everything seems to work fine, except that occasionally everything freezes.

No windows can be activated, etc. The only two things which works are the mouse pointer, which can be moved, and an ability to shut the system down using sysreq-REISUB (No I cannot open a separate tty using ctrl-alt-f1).

This tells me that at least some processes are still running. When the system comes back online nothing has been logged in the logs - at least nothing I have found.

I cannot rule out a hardware malfunction, although my windows installation never freezes or crashes. First and foremost I'd like some ideas on how to diagnose this.

---

### Post by oldos2er on 2016-01-07
To check your RAM, run memtest from the grub menu. It's best to let it run overnight if possible.

To check your hard disks, use smartctl. See [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

Can you list your hardware specs, and whether this a desktop or laptop?

---

### Post by anton.lauridsen on 2016-01-08
I ran a short smartctl test on both drives, neither reported any errors. The history of both drives list no errors.

I'll run a memtest tonight.

Its a desktop, windows on one disk (with grub2), and Ubuntu on the other.

output of lspci: 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

---

