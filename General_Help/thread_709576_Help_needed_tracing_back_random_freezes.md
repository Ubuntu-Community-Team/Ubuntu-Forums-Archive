---
title: "Help needed tracing back random freezes"
date: 2008-02-27
forum: General Help
---

### Post by Nergar on 2008-02-27
I am running Ubuntu 7.10 64bit edition and i am experiencing random Lockups, The thing is i cant find the problem and i need help tracing it back. All the hardware is new except for the WLAN PCI card and IDE HDD (used for backups) and both worked well in the old PC. The luckups happen in both 32 and 64 bits, but I haven't tried another distro.

Any help is apreciated

I'll be posting post-crash system logs later.

My hardware
```
daniel@nergar-pc:~$ lsusb
Bus 001 Device 004: ID 0d62:001c Darfon Electronics Corp. 
Bus 001 Device 005: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

```

```
daniel@nergar-pc:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

```

CPU: Intel Core 2 Quad Q6600 @ 2.4
Ram: 2  Kingston DDR2 2GB
Motherboard: Asus P5K-VM
GPU: Xfx Nvidia 8400 GT 512 MB
HDD: WDC WD3200AAJS

```

---

### Post by trobbins on 2008-02-28
If that's a new CPU, mainboard, and RAM, I'd run Memtest overnight if I were you.  I had random lockups due to a couple bad addresses in memory that only showed up to be a problem when doing video conversion, playing games, or other memory intensive applications.

---

### Post by marxram on 2008-04-09
Hi,

I'm running Kubuntu 7.10 gutsy 64 bit since yesterday. With the 32 Bit Version all worked well (with 4 GB RAM). To use 8GB RAM I installed the 64bit Version. An in the same time the new RAMs.

Now my Network hangs some Minutes after booting up." ifconfig" states, that Networking with eth0 works. Even /etc/init.d/networking restart doesnt do anything! I removed the network-manager an configured everything in /etc/network/interfaces - Without any effects

 My networkCard is the same: Marvell 88E8056 PCI-E.

Im trying to reduce RAM to 4GB and test again... I would be very happy about solutions.

---

### Post by marxram on 2008-04-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138611](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138611) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I now have found that ther Kernel Module sky2 is still buggy, wich is the reason for my freezes...

I dont know wheather that helps you.. But now I know what my problem is

On top you see the link to the bug-description

---

