---
title: "General desktop problems, will upgrading help?"
date: 2017-12-20
forum: General Help
---

### Post by primuspaul on 2017-12-20
I am having some trouble with Ubuntu. I installed it about a year ago so I think it is version 16.04 (will check and get back to you once I get home). It's a decent desktop with an i3 CPU (will verify once home), an SSD and a dedicated GPU.

Problems include:
1. Mouse cursor turns to "spinning" (I guess it's linux's version of Windows's hourglass) image and doesn't stop.

2. VLC often crashes in the background and has to be killed with system processes screen (which by the way does not open via ctrl+alt+esc or any other combination I could find and has to be opened from the menu). After killing it, the same file opens without issue, leading me to believe that the cause is not the file, but system unpredictability.

3. Sometimes the system outright freezes, though this only happens 1-2 times a month that I noticed. However, I am not the main user of the computer.

4. Sometimes moving files to another drive (like a flash drive) does not pop up any progress screen showing % complete or ETA.

5. I keep getting that error each startup about trying to update some font and how it failed.

Will upgrading to the latest version of Ubuntu help? Is it safe?
What is a reliable program to back up the OS to a USB HDD so that it can be restored if the upgrade goes wrong? I prefer something that can boot from a USB drive and backs up the partition efficiently (if the partition is sized to 200GB with 50GB used, I prefer the backup file to be 50GB, not 200GB).

---

### Post by ajgreeny on 2017-12-20
What is the dedicated GPU?

16.04 has some difficulties with certain proprietary drivers for graphic cards, and it would be good to know what we are dealing with.
When installing did you allow it to install any updates available and also add third party packages, as that may have added a graphics driver that is not working properly?

Let's see the output of **lspci** in terminal and we can move on from there.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by primuspaul on 2017-12-20
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation H55 Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation G94 [GeForce 9600 GSO 512] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
06:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)

```

GPU is [GeForce 9600 GSO 512], that's from Terminal. I think it's a Zotac card. I don't remember if I did any updates.

---

