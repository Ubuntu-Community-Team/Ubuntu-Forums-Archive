---
title: "ubuntu 20.04, second monitor on hdmi port not detected"
date: 2020-09-10
forum: General Help
---

### Post by themeditationcenter on 2020-09-10
I have kubuntu 20.04 installed. When I connect my HDMI external monitor, it just doesnt recognize. I did a reboot, replaced the cable and all other regular checks but no use.

My xrandr output below:
```

        xrandr: Failed to get size of gamma for output default
        Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
        default connected primary 1920x1080+0+0 0mm x 0mm
           1920x1080     77.00* 
```

My issue is exactly like that mentioned [here]("https://askubuntu.com/posts/1274212/edit")

---

### Post by CelticWarrior on 2020-09-10
Welcome.

Please post hardware specifications.

---

### Post by themeditationcenter on 2020-09-10
lspci output:

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Starship/Matisse IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:05.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 7
01:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
02:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset USB 3.1 XHCI Controller (rev 01)
02:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset SATA Controller (rev 01)
02:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Bridge (rev 01)
03:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
03:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
03:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
05:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
07:00.0 VGA compatible controller: NVIDIA Corporation Device 1f14 (rev a1)
07:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
07:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1)
07:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller (rev a1)
08:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function
09:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP
09:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP
09:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller
09:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller
0a:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
0b:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
```

Let me know if you need any other info. Thank you for looking into this issue.

---

### Post by themeditationcenter on 2020-09-10
My lshw output can be found [here]("https://paste.ubuntu.com/p/d33zwGxTBV/")

---

### Post by CelticWarrior on 2020-09-10
You have Nvidia Graphics.
So...
If you installed Kubuntu with the option to also install drivers, etc. and it still shows "[COLOR=#000000]display UNCLAIMED" that means Secure Boot is enabled. Just disabled it and hopefully the drivers will be loaded and everything works as expected.
If you didn't select the option mentioned then you need to open Additional Drivers, select and apply the recommended Nvidia drivers (and disable Secure Boot as well).[/COLOR]

---

### Post by themeditationcenter on 2020-09-10
Thanks a billion. This worked. No words to express my gratitude.

---

