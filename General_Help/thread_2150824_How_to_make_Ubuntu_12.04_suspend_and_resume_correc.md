---
title: "How to make Ubuntu 12.04 suspend and resume correctly."
date: 2013-06-02
forum: General Help
---

### Post by arunb on 2013-06-02
Hi,

I have been searching the internet for solutions to solve the suspend and resume problem in Ubuntu 12.04. I have updated the system but still suspend/resume does not work correctly.

Can anyone help please...

thanks
a

---

### Post by ahallubuntu on 2013-06-02
~

---

### Post by sgage on 2013-06-02
> **arunb said:**
> Hi,

I have been searching the internet for solutions to solve the suspend and resume problem in Ubuntu 12.04. I have updated the system but still suspend/resume does not work correctly.

Can anyone help please...

thanks
a

If you have an nvidia graphics card, and are not using the propietary drivers, you might try that. I have never been able to resume from suspend with nouveau, but no problem with nvidia drivers.

---

### Post by arunb on 2013-06-02
the contents of lspci
> arunb@arunb-Lenovo-G580:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
arunb@arunb-Lenovo-G580:~$ 


The system monitor screen says..
Release 12.04 (precise) 64-bit
Kernel Linux 3.5.0-31-generic
GNOME 3.4.2

---

