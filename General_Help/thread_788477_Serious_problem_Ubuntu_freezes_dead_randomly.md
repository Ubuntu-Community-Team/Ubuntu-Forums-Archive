---
title: "Serious problem: Ubuntu freezes dead randomly"
date: 2008-05-09
forum: General Help
---

### Post by wolf037 on 2008-05-09
Hi, I have a dual boot system, which previously had guadalinex(a linux version based on ubuntu edgy). Since I decided to switch to hardy, i´ve been having these random freezes. The system freezes and locks up for no aparent reason every now and then, and not even the virtual consoles work, even the mouse pointer freezes. When this happen, it does not recover, even after hours, and I have to hard reboot. All that hard rebooting is destroying my disks logically - i have to run fsck manually each time I restart.

Even though this has the symptoms of a hard drive failure, I´m not convinced, since I didn´t have any problems with the previous version of linux nor the current version of windows xp.

I need to hunt this bug down, so I need advice from people with experience in the matter.

The bug seems totally random. The machine can freeze right away after booting, or after two days usage... I can´t find a pattern, so its not a specific program that causes it.

To root out HDD failure, I need to know how to identify in the logs what could constitute a hardware failure, and diagnose it within linux(the root drive is in ext3 format, so I can´t use windows to diagnose it).

Here is a system summary:


Processor: DualCore AMD Athlon 64 X2, 2015 MHz (10 x 202) 3800+
Motherboard:Asus A8N-E  (3 PCI, 2 PCI-E x1, 1 PCI-E x4, 1 PCI-E x16, 4 DDR DIMM, Audio, Gigabit LAN)
Chipset: nVIDIA nForce4 Ultra, AMD Hammer
System Memmory: 2048 MB  (PC3200 DDR SDRAM)
Bios: Award (11/25/05)
3d Graphics card: NVIDIA GeForce 7300 GS  (512 MB)
Hard Disks:
-HDS728080PLA380  (80 GB, 7200 RPM, SATA-II)
-SAMSUNG HD400LJ SCSI Disk Device  (400 GB, 7200 RPM, SATA-II)
-SAMSUNG HD400LJ  (400 GB, 7200 RPM, SATA-II)
-SAMSUNG HD501LJ  (500 GB, 7200 RPM, SATA-II)
-SAMSUNG HD501LJ  (500 GB, 7200 RPM)
Note: Two of the hard disks are on a pci-to-sata controller card. The root partition is on a regular hard disk which is not attached to that card.

Please inform me which kinds of logs do you need posted to help me diagnose the problem.(I´m a newbie linux user, so I get lost inside the logs)

Also, I know other people may have had similar problems. If you can point me to other relevant threads about it, I´ll read em too.

---

