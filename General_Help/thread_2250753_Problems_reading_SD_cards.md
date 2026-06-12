---
title: "Problems reading SD cards"
date: 2014-10-30
forum: General Help
---

### Post by danielsender on 2014-10-30
I have a Dell Precision M90 running 14.04.1. In order to have the machine seeing the SD card inserted in the internal reader I type:

sudo modprobe -r r852
sudo modprobe -r sdhci_pci
sudo modprobe r852
sudo modprobe sdhci_pci

and I see the cards and can read and write in it. However if I unmount and remove the card, the next time I insert the card it won't be seen by the system. So my question is how do I do it at boot time and be permanent?

Thanks.

---

### Post by danielsender on 2014-11-04
anybody?

---

### Post by d4m1r on 2014-11-04
You shouldn't have to do all that....You should be able to use the SD card just like under Windows. I.e, you pop in a card, it gets mounted automatically, you can read/write to it, eject it, and even pop it back in and do that all over again.

Who told you/why are you running those commands? If you can provide us the exact make/model of your card reader (probably not made by Dell directly), we can help you try to find the proper drivers for it that would let you do all of the above...

---

### Post by danielsender on 2014-11-04
That is exactly the problem, nothing is happening automatically - I found on a site that those modules would enable the card readers, and they do, however they are not permanent.

My system is a Dell Precision M90 running 14.04.1, and the output of lspci (for the card reader manufacturer) is:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G71GLM [Quadro FX 2500M] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

Many thanks for your time.

Daniel

---

### Post by danielsender on 2014-11-11
Am I the only one who is having this issue?

---

