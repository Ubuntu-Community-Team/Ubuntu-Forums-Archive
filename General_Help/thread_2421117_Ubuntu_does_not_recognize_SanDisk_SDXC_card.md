---
title: "Ubuntu does not recognize SanDisk SDXC card"
date: 2019-06-16
forum: General Help
---

### Post by yoramdavid on 2019-06-16
Hi, I purchased a new 128 GB SanDisk SDXC card, and when I insert it in the laptop, it does not appear on the file manager.
The card works on the camera and other 64GB  SanDisk SDXC cards work on the laptop.

 I did some research and tested a few commands, which I paste here:
```
lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 13d3:5188 IMC Networks 
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 003 Device 006: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
lspci -v  # a long output
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: ie31200_edac

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 26
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f6000000-f70fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. 4th Gen Core Processor Integrated Graphics Controller
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
	Subsystem: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at f7a14000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family USB xHCI
	Flags: bus master, medium devsel, latency 0, IRQ 31
	Memory at f7a00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family MEI Controller
	Flags: bus master, fast devsel, latency 0, IRQ 36
	Memory at f7a1e000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei_me
	Kernel modules: mei_me

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family USB EHCI
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f7a1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 39
	Memory at f7a10000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cfe00000-cfffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f21fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: f7900000-f79fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7800000-f78fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family USB EHCI
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7a1b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. HM86 Express LPC Controller
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 32
	I/O ports at f0b0 [size=8]
	I/O ports at f0a0 [size=4]
	I/O ports at f090 [size=8]
	I/O ports at f080 [size=4]
	I/O ports at f060 [size=32]
	Memory at f7a1a000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family SMBus Controller
	Flags: medium devsel, IRQ 255
	Memory at f7a19000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f040 [size=32]
	Kernel modules: i2c_i801

01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 850M] (rev a2)
	Subsystem: ASUSTeK Computer Inc. GM107M [GeForce GTX 850M]
	Flags: bus master, fast devsel, latency 0, IRQ 37
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

04:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-N 7260
	Flags: bus master, fast devsel, latency 0, IRQ 38
	Memory at f7900000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
	Subsystem: ASUSTeK Computer Inc. RTL8411B PCI Express Card Reader
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f7815000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at f7800000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci

05:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	I/O ports at d000 [size=256]
	Memory at f7814000 (64-bit, non-prefetchable) [size=4K]
	Memory at f7810000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

```
sudo parted -ls
Modelo: ATA Samsung SSD 850 (scsi)
Disco /dev/sda: 1024GB
Tamanho de sector (lógico / físico): 512B/512B
Tabela de Partições: gpt
Sinalizadores do Disco: 

Número  Início  Final   Tamanho  Sistema de ficheiros  Nome                  Sinalizadores
 1      1049kB  538MB   537MB    fat32                 EFI System Partition  boot, esp
 2      538MB   51,7GB  51,2GB   ext4
 4      51,7GB  1011GB  960GB    ext4
 3      1011GB  1024GB  12,8GB   linux-swap(v1)        Swap


Modelo: ATA SanDisk SSD U100 (scsi)
Disco /dev/sdb: 24,0GB
Tamanho de sector (lógico / físico): 512B/512B
Tabela de Partições: gpt
Sinalizadores do Disco: 

Número  Início  Final   Tamanho  Sistema de ficheiros  Nome  Sinalizadores
 1      1049kB  24,0GB  24,0GB   ext4                  Temp

```

```
sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE
MODEL            NAME   FSTYPE   LABEL MOUNTPOINT         SIZE
                 loop0  squashfs       /snap/core/6964   88,4M
                 loop1  squashfs       /snap/core/6673   89,3M
                 loop2  squashfs       /snap/vuze-vs/3  280,2M
                 loop3  squashfs       /snap/core/6818   89,4M
Samsung SSD 850  sda                                    953,9G
                 &#9500;&#9472;sda1 vfat           /boot/efi          512M
                 &#9500;&#9472;sda2 ext4           /                 47,7G
                 &#9500;&#9472;sda3 swap           [SWAP]            11,9G
                 &#9492;&#9472;sda4 ext4           /home            893,8G
SanDisk SSD U100 sdb                                     22,4G
                 &#9492;&#9472;sdb1 ext4     Temp  /home/yoram/Temp  22,4G
DVD-RAM UJ8E2 S  sr0                                     1024M

```

My ubuntu version is:
```
lsb_release -a
LSB Version:	core-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic

```

Any help, please?
Thank you.
Yoram

---

### Post by ajgreeny on 2019-06-16
A memory card of that size is most likely formatted with an exfat filesystem which is not usable in Linux without installing the two exfat packages in the repos with command ```
sudo apt install exfat-fuse exfat-utils
```
Try that, and if still unsuccessful come back again and we can look deeper.

---

### Post by yoramdavid on 2019-06-16
Thank you.
Says it is already installed:

```
sudo apt install exfat-fuse exfat-utils
[sudo] senha para yoram: 
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
exfat-fuse is already the newest version (1.2.8-1).
exfat-utils is already the newest version (1.2.8-1).
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.

```

---

### Post by kurt18947 on 2019-06-16
My thought would have been the same as ajgreeny, exfat but if those two files are already installed perhaps not. If it were me I'd probably try to format the card to FAT32 or ext4 if the card would be used in linux machines only. FAT32 should work fine as long as you don't try to copy files larger than 4 GB. I tend toward FAT32 unless I want the permissions associated with ext4.

---

### Post by yoramdavid on 2019-06-24
> **kurt18947 said:**
> My thought would have been the same as ajgreeny, exfat but if those two files are already installed perhaps not. If it were me I'd probably try to format the card to FAT32 or ext4 if the card would be used in linux machines only. FAT32 should work fine as long as you don't try to copy files larger than 4 GB. I tend toward FAT32 unless I want the permissions associated with ext4.

Thank you.
But how do I format the card if I cannot see it on the computer? Not even under gparted.

---

### Post by kurt18947 on 2019-06-30
Sorry for the delay replying. Could you try the card in another machine, perhaps a friend's Windows machine or something? Make sure the card is not faulty. If the card is seen on a Windows machine perhaps reformat it to FAT32 and see if it then appears on your machine. I have very little experience with exFat on Ubuntu but what experience I did have the card was seen and functioned using the utilities mentioned above.

---

### Post by yoramdavid on 2019-07-06
Any further help, anyone?

---

### Post by Ralph L on 2019-07-13
I have the same problem as you--laptop won't detect SanDisk 128GB micro sd put into (with SD adapter) in to card slot.  Running Xubuntu on Acer Aspire E15. See: [https://ubuntuforums.org/showthread.php?t=2422796](https://ubuntuforums.org/showthread.php?t=2422796) .  

However, if I put the microSd card in a USB adapter and insert it in the USB port, everything works.  Don't know that this helps, but it is a workaround.  Oh, I formatted the card as NTSF.

---

### Post by alainhenry on 2019-07-15
I have the same issue with a 64GB SD card. Under windows, my computer can read it without problem. Under Linux Ubuntu 18.04, the same computer does not detect it at all. But it detects 32 GB SD cards. And I have installed the exfat packages. The SD cards have been formatted on a Fujifilm XT-20 camera.

---

### Post by Ralph L on 2019-07-17
I am running Xubuntu 18.04 and have installed exfat-fuse, exfat-utils.  I can't get Xubuntu to detect my 128G microSD card (in an adapter), when I put it in the SDcard slot on my Acer Aspire E15.  It detects and works fine under Windows 10.  After a number of experiments with different formats and different size microSD cards, I have found that Xubuntu will recognize any 64G card no matter what the format--exfat, fat32, exp4, ntfs.  However, it won't detect any 128G card, no matter what the format--exfat, fat32, exp4, ntfs.  The 128G card won't even pop into the /dev folder as mmcblk0 or mmcblk0p1 as it should.  

It looks to me like the SDcard slot driver was written to support sizes up to only 64G. Maybe the author thought SDcards would never get bigger than that.  However, with cards currently available at 1TB (Sandisk), and people working on even bigger ones, this needs to be fixed.  As near as I can see the exfat software has nothing to do with the problem.  It is the driver.

Anybody else have any ideas on this????

---

