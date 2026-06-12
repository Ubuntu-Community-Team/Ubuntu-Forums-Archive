---
title: "HP touchsmart tx2 wireless switch is off"
date: 2012-11-16
forum: General Help
---

### Post by Anon1992 on 2012-11-16
Hi, I'm really new to linux so I decided to try ubuntu 12.10 on my old HP touchsmart tx2 laptop.
One big problem is the wireless switch (light) is off doesn't turn when I turn it.
I did some research and found some solution but I live in a dorm so I can't go plug my laptop to a router with ethernet cable.
Is there anything I can do to fix this? I really like it but I don't have an internet access :(.
Thank you

---

### Post by Anon1992 on 2012-11-17
Forgot to mention that the chip is Broadcom BCM4312
Is there a way to fix this without wired internet?

---

### Post by idoitprone on 2012-11-17
let check you kernel modules

```
lspci -nnk
```the first module you can try is wl

```
sudo modprobe wl
```and you need to download the package

firmware-b43-installer 
[http://packages.ubuntu.com/quantal/firmware-b43-installer](http://packages.ubuntu.com/quantal/firmware-b43-installer)

or pop in the live cd and try to download it from there
just make sure you ave the proper repos enable to download from live cd or usb

---

### Post by Anon1992 on 2012-11-17
> **idoitprone said:**
> let check you kernel modules

```
lspci -nnk
```the first module you can try is wl

```
sudo modprobe wl
```and you need to download the package

firmware-b43-installer 
[http://packages.ubuntu.com/quantal/firmware-b43-installer](http://packages.ubuntu.com/quantal/firmware-b43-installer)

or pop in the live cd and try to download it from there
just make sure you ave the proper repos enable to download from live cd or usb

Hi, thank you for the suggestion but it doesn't seem to work
here is the log

anon@anon-HP-TouchSmart-tx2-Notebook-PC:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602]
	Kernel modules: shpchp
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ohci_hcd
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ehci_hcd
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ohci_hcd
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3a)
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: ohci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control [1022:1303]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics] [1002:9612]
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: radeon
	Kernel modules: radeon
08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137c]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:3045]
	Kernel driver in use: r8169
	Kernel modules: r8169
anon@anon-HP-TouchSmart-tx2-Notebook-PC:~$ sudo modprobe wl
[sudo] password for anon:
FATAL: Module wl not found.


PS For the download part I'm sorry I don't understand which file to download or what to do, I'm really new to this.
Can you please explain?
Thank you

---

### Post by Anon1992 on 2012-11-17
Bump
Anyone?

---

### Post by Favux on 2012-11-18
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access)

[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-card-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-card-bcm43xx)

---

