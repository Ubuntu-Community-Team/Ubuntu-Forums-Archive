---
title: "ubuntu 20.04 crashes after waking up from suspend"
date: 2021-08-19
forum: General Help
---

### Post by compay2k on 2021-08-19
Hello, 

I just installed Ubuntu 20.04 besides a windows 10 on my laptop, and when I suspend ubuntu (either keyboard function or closing the lid), the wake up crashes my laptop with the following message :

```
Bluetooth: hci0: Reading supported features failed (-16) 
Bluetooth: hci0: Setting Intel telemetry ddc write event mask failed (-95) 
```

By the way, I cannot activate bluetooth, despite the led is on on the computer. (it was actually soft-blocked, unblocked it since but still the same issue)

I checked various bluetooth settings but without any result...

Does anybody have an idea ? :)

Thank you 

Here's my hardware configuration : 

```
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [8086:1910] (rev 07)
    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers [1458:2464]
    Kernel driver in use: skl_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) [8086:1901] (rev 07)
    Kernel driver in use: pcieport
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 530 [8086:191b] (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Gigabyte Technology Co., Ltd HD Graphics 530 [1458:2464]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller [8086:a12f] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller [1458:2464]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
00:14.2 Signal processing controller [1180]: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem [8086:a131] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family Thermal Subsystem [1458:2464]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:16.0 Communication controller [0780]: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 [8086:a13a] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family MEI Controller [1458:2464]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation HM170/QM170 Chipset SATA Controller [AHCI Mode] [8086:a103] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd HM170/QM170 Chipset SATA Controller [AHCI Mode] [1458:2464]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #2 [8086:a111] (rev f1)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #3 [8086:a112] (rev f1)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #5 [8086:a114] (rev f1)
    Kernel driver in use: pcieport
00:1d.0 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #13 [8086:a11c] (rev f1)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation HM170 Chipset LPC/eSPI Controller [8086:a14e] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd HM170 Chipset LPC/eSPI Controller [1458:2464]
00:1f.2 Memory controller [0580]: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller [8086:a121] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family Power Management Controller [1458:2464]
00:1f.3 Audio device [0403]: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller [8086:a170] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family HD Audio Controller [1458:2464]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1f.4 SMBus [0c05]: Intel Corporation 100 Series/C230 Series Chipset Family SMBus [8086:a123] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family SMBus [1458:2464]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] [10de:1c20] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd GP106M [GeForce GTX 1060 Mobile] [1458:2464]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GP106 High Definition Audio Controller [10de:10f1] (rev ff)
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader [10ec:522a] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader [10ec:522a]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
03:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Dual Band Wireless-AC 8260 [8086:1010]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242]
    Subsystem: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
05:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM951/PM951 [144d:a802] (rev 01)
    Subsystem: Samsung Electronics Co Ltd NVMe SSD Controller SM951/PM951 [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
```

---

### Post by Timothy Taylor on 2021-08-19
Suspend freezes my system too and this has been [reported by others]("https://ubuntuforums.org/showthread.php?t=2465731&p=14053376#post14053376").
I've stopped using suspend until this is fixed.

---

