---
title: "Some Live CD/DVD do not load"
date: 2015-08-12
forum: General Help
---

### Post by Canaryguy on 2015-08-12
Hello,

I have a netbook Toshiba Satellite with two partitions, one for Ubuntu 15.04 x64 and another for Windows.

I created a live CD with Lubuntu 15.04 for a friend and I wanted to test it first on my computer but the CD does not load. I tried with both versions x32 and x64. 

I also tried with Ubuntu Mate 15.04 x32 and x64 and none of them start neither with a DVD nor with a Pendrive (using Unetbootin).

I tried with another distribution, AntiX, and with this distribution I could load the live CD. I don't know why Lubuntu or Ubuntu Mate don't load.

Does anybody know the cause of the problem?

Thanks in advance.

---

### Post by mörgæs on 2015-08-13
Please begin with a complete hardware description.

---

### Post by Canaryguy on 2015-08-13
**Output of lspci**

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
07:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
09:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265]

---

### Post by mörgæs on 2015-08-15
I don't see problems with hardware support.
Maybe some other posters have an idea...?

---

