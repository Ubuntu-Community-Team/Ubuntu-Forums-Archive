---
title: "No Audio"
date: 2023-03-30
forum: General Help
---

### Post by Mr Fredrick on 2023-03-30
Hi All,

Since swapping to the Nvidia 515 driver I no longer have audio and the outputs listed in settings do not list my audio device. 

```
lspci
07:00.1 Audio device: NVIDIA Corporation TU116 High Definition Audio Controller (rev a1)
```

Above is the output from lspci.

How can I overcome/trouble shoot this problem? Thanks in advance,

MrFred.

---

### Post by T.J. on 2023-03-30
> **Mr Fredrick said:**
> Hi All,

Since swapping to the Nvidia 515 driver I no longer have audio and the outputs listed in settings do not list my audio device. 

```
lspci
07:00.1 Audio device: NVIDIA Corporation TU116 High Definition Audio Controller (rev a1)
```

Above is the output from lspci.

How can I overcome/trouble shoot this problem? Thanks in advance,

MrFred.

That is not enough significant information to help.  Please use: 

```
lspci --vnn
```

It will provide a readout of the devices, their bindings, and the drivers in use.  

For example: 
```

[FONT=monospace][COLOR=#000000]0d:00.3 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller [1022:145[/COLOR]
7] 
        Subsystem: Gigabyte Technology Co., Ltd Family 17h (Models 00h-0fh) HD Audio Controller [1458:a0c3] 
        Flags: bus master, fast devsel, latency 0, IRQ 104, IOMMU group 23 
        Memory at fc900000 (32-bit, non-prefetchable) [size=32K] 
        Capabilities: <access denied> 
        Kernel driver in use: snd_hda_intel 
        Kernel modules: snd_hda_intel

[/FONT]

```

You can then use that information to help diagnose your problem.  Drop a comment if there is anything I can do to help.  I use Debian, rather than Ubuntu, but 98% of what I know should work for either.

---

### Post by Mr Fredrick on 2023-03-30
This is the output you requested:

```

 lspci -vnn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex [1022:1480]
	Subsystem: ASRock Incorporation Starship/Matisse Root Complex [1849:1480]
	Flags: fast devsel

00:01.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge [1022:1482]
	Flags: fast devsel

00:01.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge [1022:1483] (prog-if 00 [Normal decode])
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge [1022:1234]
	Flags: bus master, fast devsel, latency 0, IRQ 25
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: [disabled] [32-bit]
	Memory behind bridge: f7900000-f79fffff [size=1M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:01.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge [1022:1483] (prog-if 00 [Normal decode])
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge [1022:1234]
	Flags: bus master, fast devsel, latency 0, IRQ 26
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=0
	I/O behind bridge: f000-ffff [size=4K] [16-bit]
	Memory behind bridge: f7500000-f76fffff [size=2M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge [1022:1482]
	Flags: fast devsel

00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge [1022:1482]
	Flags: fast devsel

00:03.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge [1022:1483] (prog-if 00 [Normal decode])
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge [1022:1234]
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: e000-efff [size=4K] [16-bit]
	Memory behind bridge: f6000000-f70fffff [size=17M] [32-bit]
	Prefetchable memory behind bridge: e0000000-f20fffff [size=289M] [32-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:04.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge [1022:1482]
	Flags: fast devsel

00:05.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge [1022:1482]
	Flags: fast devsel

00:07.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge [1022:1482]
	Flags: fast devsel

00:07.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484] (prog-if 00 [Normal decode])
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484]
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: [disabled] [32-bit]
	Memory behind bridge: [disabled] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:08.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge [1022:1482]
	Flags: fast devsel

00:08.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484] (prog-if 00 [Normal decode])
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484]
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: [disabled] [32-bit]
	Memory behind bridge: f7200000-f74fffff [size=3M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:08.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484] (prog-if 00 [Normal decode])
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484]
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: [disabled] [32-bit]
	Memory behind bridge: f7800000-f78fffff [size=1M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:08.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484] (prog-if 00 [Normal decode])
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] [1022:1484]
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: [disabled] [32-bit]
	Memory behind bridge: f7700000-f77fffff [size=1M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 61)
	Subsystem: ASRock Incorporation FCH SMBus Controller [1849:790b]
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c_piix4, sp5100_tco

00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 51)
	Subsystem: ASRock Incorporation FCH LPC Bridge [1849:790e]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 0 [1022:1440]
	Flags: fast devsel

00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 1 [1022:1441]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 2 [1022:1442]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 3 [1022:1443]
	Flags: fast devsel
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 4 [1022:1444]
	Flags: fast devsel

00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 5 [1022:1445]
	Flags: fast devsel

00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 6 [1022:1446]
	Flags: fast devsel

00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 7 [1022:1447]
	Flags: fast devsel

01:00.0 Non-Volatile memory controller [0108]: ADATA Technology Co., Ltd. XPG SX8200 Pro PCIe Gen3x4 M.2 2280 Solid State Drive [1cc1:8201] (rev 03) (prog-if 02 [NVM Express])
	Subsystem: ADATA Technology Co., Ltd. XPG SX8200 Pro PCIe Gen3x4 M.2 2280 Solid State Drive [1cc1:8201]
	Flags: bus master, fast devsel, latency 0, IRQ 40, NUMA node 0
	Memory at f7900000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: nvme
	Kernel modules: nvme

02:00.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset USB 3.1 XHCI Controller [1022:43d5] (rev 01) (prog-if 30 [XHCI])
	Subsystem: ASRock Incorporation 400 Series Chipset USB 3.1 XHCI Controller [1849:43d0]
	Flags: bus master, fast devsel, latency 0, IRQ 64
	Memory at f76a0000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci

02:00.1 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset SATA Controller [1022:43c8] (rev 01) (prog-if 01 [AHCI 1.0])
	Subsystem: ASRock Incorporation 400 Series Chipset SATA Controller [1849:43c8]
	Flags: bus master, fast devsel, latency 0, IRQ 39
	Memory at f7680000 (32-bit, non-prefetchable) [size=128K]
	Expansion ROM at f7600000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

02:00.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Bridge [1022:43c6] (rev 01) (prog-if 00 [Normal decode])
	Subsystem: ASRock Incorporation 400 Series Chipset PCIe Bridge [1849:43c6]
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=0
	I/O behind bridge: f000-ffff [size=4K] [16-bit]
	Memory behind bridge: f7500000-f75fffff [size=1M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

03:00.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01) (prog-if 00 [Normal decode])
	Subsystem: ASRock Incorporation 400 Series Chipset PCIe Port [1849:43c7]
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Bus: primary=03, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: [disabled] [32-bit]
	Memory behind bridge: [disabled] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

03:01.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01) (prog-if 00 [Normal decode])
	Subsystem: ASRock Incorporation 400 Series Chipset PCIe Port [1849:43c7]
	Flags: bus master, fast devsel, latency 0, IRQ 37
	Bus: primary=03, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: f000-ffff [size=4K] [16-bit]
	Memory behind bridge: f7500000-f75fffff [size=1M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

03:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] 400 Series Chipset PCIe Port [1022:43c7] (rev 01) (prog-if 00 [Normal decode])
	Subsystem: ASRock Incorporation 400 Series Chipset PCIe Port [1849:43c7]
	Flags: bus master, fast devsel, latency 0, IRQ 38
	Bus: primary=03, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: [disabled] [32-bit]
	Memory behind bridge: [disabled] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Capabilities: <access denied>
	Kernel driver in use: pcieport

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Flags: bus master, fast devsel, latency 0, IRQ 36
	I/O ports at f000 [size=256]
	Memory at f7504000 (64-bit, non-prefetchable) [size=4K]
	Memory at f7500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

07:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU116 [GeForce GTX 1660] [10de:2184] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Gigabyte Technology Co., Ltd TU116 [GeForce GTX 1660] [1458:3fc7]
	Flags: bus master, fast devsel, latency 0, IRQ 79
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

07:00.1 Audio device [0403]: NVIDIA Corporation TU116 High Definition Audio Controller [10de:1aeb] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd TU116 High Definition Audio Controller [1458:3fc7]
	Flags: bus master, fast devsel, latency 0, IRQ 81
	Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

07:00.2 USB controller [0c03]: NVIDIA Corporation TU116 USB 3.1 Host Controller [10de:1aec] (rev a1) (prog-if 30 [XHCI])
	Subsystem: Gigabyte Technology Co., Ltd TU116 USB 3.1 Host Controller [1458:3fc7]
	Flags: fast devsel, IRQ 66
	Memory at f2000000 (64-bit, prefetchable) [size=256K]
	Memory at f2040000 (64-bit, prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci

07:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU116 USB Type-C UCSI Controller [10de:1aed] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd TU116 USB Type-C UCSI Controller [1458:3fc7]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f7084000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia-gpu
	Kernel modules: i2c_nvidia_gpu

08:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function [1022:148a]
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function [1022:148a]
	Flags: fast devsel
	Capabilities: <access denied>

09:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP [1022:1485]
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP [1022:1485]
	Flags: fast devsel
	Capabilities: <access denied>

09:00.1 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP [1022:1486]
	Subsystem: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP [1022:1486]
	Flags: bus master, fast devsel, latency 0, IRQ 76
	Memory at f7300000 (32-bit, non-prefetchable) [size=1M]
	Memory at f7408000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ccp
	Kernel modules: ccp

09:00.3 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller [1022:149c] (prog-if 30 [XHCI])
	Subsystem: ASRock Incorporation Matisse USB 3.0 Host Controller [1849:7914]
	Flags: bus master, fast devsel, latency 0, IRQ 67
	Memory at f7200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci

09:00.4 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller [1022:1487]
	Subsystem: ASRock Incorporation Starship/Matisse HD Audio Controller [1849:7893]
	Flags: bus master, fast devsel, latency 0, IRQ 83
	Memory at f7400000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

0a:00.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 51) (prog-if 01 [AHCI 1.0])
	Subsystem: ASRock Incorporation FCH SATA Controller [AHCI mode] [1849:7901]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f7800000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

0b:00.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 51) (prog-if 01 [AHCI 1.0])
	Subsystem: ASRock Incorporation FCH SATA Controller [AHCI mode] [1849:7901]
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at f7700000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

```

---

### Post by SeijiSensei on 2023-03-30
My guess is that the NVIDIA driver is not installed. Run "sudo ubuntu-drivers" and see what happens.

---

### Post by T.J. on 2023-03-30
> **Mr Fredrick said:**
> This is the output you requested:


07:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU116 [GeForce GTX 1660] [10de:2184] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd TU116 [GeForce GTX 1660] [1458:3fc7]
    Flags: bus master, fast devsel, latency 0, IRQ 79
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

07:00.1 Audio device [0403]: NVIDIA Corporation TU116 High Definition Audio Controller [10de:1aeb] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd TU116 High Definition Audio Controller [1458:3fc7]
    Flags: bus master, fast devsel, latency 0, IRQ 81
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

07:00.2 USB controller [0c03]: NVIDIA Corporation TU116 USB 3.1 Host Controller [10de:1aec] (rev a1) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd TU116 USB 3.1 Host Controller [1458:3fc7]
    Flags: fast devsel, IRQ 66
    Memory at f2000000 (64-bit, prefetchable) [size=256K]
    Memory at f2040000 (64-bit, prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

07:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU116 USB Type-C UCSI Controller [10de:1aed] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd TU116 USB Type-C UCSI Controller [1458:3fc7]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f7084000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia-gpu
    Kernel modules: i2c_nvidia_gpu


Your device has a driver loaded: snd_hda_intel.   That's great.  The device is recognized.





Does your desktop GUI recognize the device as present, and is it muted?  Please use pavucontrol to check which port is assigned as output. Most video cards these days have more than one. Ex:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291990&stc=1[/IMG]
If that is not it, I did find this as a documented issue from 2021:
[https://forums.developer.nvidia.com/t/no-hdmi-audio-on-nvidia-1660-super-driver-460-ubuntu-20-10/165785](https://forums.developer.nvidia.com/t/no-hdmi-audio-on-nvidia-1660-super-driver-460-ubuntu-20-10/165785)

---

### Post by Mr Fredrick on 2023-03-30
These are the outputs as requested:

```

~$ sudo ubuntu-drivers

Usage: ubuntu-drivers [OPTIONS] COMMAND [ARGS]...

Options:
  --gpgpu              gpgpu drivers
  --free-only          Only consider free packages
  --package-list PATH  Create file with list of installed packages (in install
                       mode)
  --no-oem             Do not include OEM enablement packages (these enable an
                       external archive)  [default: False]
  -h, --help           Show this message and exit.

Commands:
  autoinstall  Deprecated, please use "install" instead
  debug        Print all available information and debug data about drivers.
  devices      Show all devices which need drivers, and which packages...
  install      Install a driver [driver[:version][,driver[:version]]]
  list         Show all driver packages which apply to the current system.
  list-oem     Show all OEM enablement packages which apply to this system
```

---

### Post by MAFoElffen on 2023-03-30
Lets skip ahead a few pages and get down to some diagnostics that will tell us what is going on...

Start an application that should be playing output to "something"... This step is important, because the "command below" looks for and at the audio streams being played to analyze them.

Then in a terminal, do this:
```

pacmd list-sink-inputs

```
The output is going to be detailed like this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ pacmd list-sink-inputs
1 sink input(s) available.
    index: 45
    driver: <protocol-native.c>
    flags: 
    state: RUNNING
    sink: 0 <alsa_output.pci-0000_00_1b.0.analog-stereo>
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    muted: no
    current latency: 2000.00 ms
    requested latency: 1960.00 ms
    sample spec: float32le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    resample method: copy
    module: 12
    client: 60 <paplay>
    properties:
        media.format = "OGG (OGG Container format)"
        application.name = "paplay"
        media.name = "/usr/share/sounds/ubuntu/ringtones/Harmonics.ogg"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "35"
        application.process.id = "51231"
        application.process.user = "mafoelffen"
        application.process.host = "Mikes-ThinkPad-T520"
        application.process.binary = "pacat"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "23043aec7ab3495381a8778a1b2b4fda"
        module-stream-restore.id = "sink-input-by-application-name:paplay"

```
Now something like that is going to tell you the driver, which output device it is set to, the volume setting, and if it is muted or not...

Does that help you all to look at this from a different perspective? I'm patient.

---

### Post by Mr Fredrick on 2023-03-30
Hi MAFoElffen,

I played a webm file (which ran in my Firefox browser) and then the command as requested:

```

~$ pacmd list-sink-inputs
No PulseAudio daemon running, or not running as session daemon.

```

I also tried:

```

~$ pulseaudio
W: [pulseaudio] pid.c: Stale PID file, overwriting.
E: [pulseaudio] socket-server.c: bind(): Address already in use
E: [pulseaudio] module.c: Failed to load module "module-native-protocol-unix" (argument: ""): initialization failed.
E: [pulseaudio] main.c: D-Bus name org.pulseaudio.Server already taken.
```

---

### Post by MAFoElffen on 2023-03-30
Do this
```

pulseaudio -k && pulseaudio -D

```
Then retest it.

BTW -- On my way out the door to go to work.

---

### Post by #&amp;thj^% on 2023-03-30
I have working sound, and produce the same return as the OP
```
>> pacmd list-sink-inputs
No PulseAudio daemon running, or not running as session daemon.


me on Thu Mar 30 at 05:40 PM in ~ branch: (HEAD) 
>> pulseaudio
W: [pulseaudio] pid.c: Stale PID file, overwriting.
E: [pulseaudio] socket-server.c: bind(): Address already in use
E: [pulseaudio] module.c: Failed to load module "module-native-protocol-unix" (argument: ""): initialization failed.
E: [pulseaudio] main.c: D-Bus name org.pulseaudio.Server already taken.


```
The Important bits seen here:
```
systemctl --user status wireplumber pipewire
&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset>
     Active: active (running) since Thu 2023-03-30 14:36:48 MDT; 3h 7min ago
   Main PID: 622331 (wireplumber)
      Tasks: 5 (limit: 9074)
     Memory: 21.0M
        CPU: 3.414s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wirepl>
             &#9492;&#9472;622331 /usr/bin/wireplumber

Mar 30 14:36:48 me-Lenovo-Legion-5-15ARH05 systemd[8189]: Started wireplumber.s>
### and
pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: e>
     Active: active (running) since Thu 2023-03-30 11:40:32 MDT; 6h ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 8198 (pipewire)
      Tasks: 2 (limit: 9074)
     Memory: 12.4M
lines 1-23


```

---

### Post by Mr Fredrick on 2023-03-30
I ran:

pulseaudio -k && pulseaudio -D

Then started the webm file again but no audio as previously

ran this whilst webm was playing:

```

~$ pacmd list-sink-inputs
0 sink input(s) available.
```

---

### Post by #&amp;thj^% on 2023-03-30
I'm playing internet-radio:
```
pacmd list-sink-inputs
No PulseAudio daemon running, or not running as session daemon.

```
again the important bits:
```
wpctl status
PipeWire 'pipewire-0' [0.3.65, me@me-Lenovo-Legion-5-15ARH05, cookie:2393726023]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:8201]
        40. xdg-desktop-portal                  [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:8417]
        51. WirePlumber                         [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:622331]
        52. xfce4-pulseaudio-plugin             [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:8569]
        72. WirePlumber [export]                [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:622331]
        74. Strawberry device finder            [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:1042022]
        75. Strawberry                          [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:1042022]
        89. wpctl                               [0.3.65, me@me-Lenovo-Legion-5-15ARH05, pid:1223406]

Audio
 &#9500;&#9472; Devices:
 &#9474;      35. HDA NVidia                          [alsa]
 &#9474;      64. UOEOS Laptop Dock                   [alsa]
 &#9474;      65. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      33. HDA NVidia Digital Stereo (HDMI)    [vol: 0.40]
 &#9474;  *   34. UOEOS Laptop Dock Analog Surround 5.1 [vol: 0.64]
 &#9474;      36. Family 17h/19h HD Audio Controller Pro [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      61. Family 17h/19h HD Audio Controller Pro [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        81. Strawberry                                                  
             76. output_LFE      > UOEOS Laptop Dock:playback_LFE	[active]
             78. output_RL       > UOEOS Laptop Dock:playback_RL	[active]
             82. output_FR       > UOEOS Laptop Dock:playback_FR	[active]
             85. output_RR       > UOEOS Laptop Dock:playback_RR	[active]
             86. output_FC       > UOEOS Laptop Dock:playback_FC	[active]
             88. output_FL       > UOEOS Laptop Dock:playback_FL	[active]

Video
 &#9500;&#9472; Devices:
 &#9474;      53. Integrated Camera                   [v4l2]
 &#9474;      67. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   60. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-51
         1. Audio/Source  alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-51


```
Wait for MAFoElffen, I'm just driving by, and showing what I notice on my end.

---

### Post by MAFoElffen on 2023-03-31
@1fallen -- 
[s]22.04...[/s] Good catch. I didn't see that he is 22.10.
```

mafoelffen@Mikes-ThinkPad-T520:~$ pulseaudio -v
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 15.99.1
I: [pulseaudio] main.c: Page size is 4096 bytes
I: [pulseaudio] main.c: Machine ID is 23043aec7ab3495381a8778a1b2b4fda.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/mafoelffen/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-15.99.1+dfsg1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

mafoelffen@Mikes-ThinkPad-T520:~$ wpctl
[COLOR=#ff0000]Command 'wpctl' not found, but can be installed with:
sudo apt install wireplumber[/COLOR]

```
[s]22.04 is still transitional for wireplumber.[/s]

@Mr Fredrick --

Please try these commands and we shall see how it differs from these expected outputs...
```

mafoelffen@Mikes-ThinkPad-T520:~$ pulseaudio -v
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 15.99.1
I: [pulseaudio] main.c: Page size is 4096 bytes
I: [pulseaudio] main.c: Machine ID is 23043aec7ab3495381a8778a1b2b4fda.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/mafoelffen/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-15.99.1+dfsg1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

mafoelffen@Mikes-ThinkPad-T520:~$ pulseaudio --dump-conf
### Read from configuration file: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
local-server-type = user
cpu-limit = no
enable-shm = yes
flat-volumes = no
rescue-streams = yes
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-15.99.1+dfsg1/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = 
log-level = notice
resample-method = auto
avoid-resampling = no
enable-remixing = yes
remixing-use-all-sink-channels = yes
remixing-produce-lfe = no
remixing-consume-lfe = no
lfe-crossover-freq = 0
default-sample-format = s16le
default-sample-rate = 44100
alternate-sample-rate = 48000
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 4
default-fragment-size-msec = 25
enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
deferred-volume-extra-delay-usec = 0
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 200000

mafoelffen@Mikes-ThinkPad-T520:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20590 Analog [CX20590 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

mafoelffen@Mikes-ThinkPad-T520:~$ grep . /usr/share/alsa-card-profile/mixer/paths/analog-output.conf.common | grep -v '#\|;'
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
[Element External Amplifier]
switch = select
[Option External Amplifier:on]
name = output-amplifier-on
priority = 10
[Option External Amplifier:off]
name = output-amplifier-off
priority = 0
[Element Bass Boost]
switch = select
[Option Bass Boost:on]
name = output-bass-boost-on
priority = 0
[Option Bass Boost:off]
name = output-bass-boost-off
priority = 10
[Element IEC958]
switch = off
[Element IEC958 Optical Raw]
switch = off
[Element Analog Output]
enumeration = select
[Option Analog Output:Speakers]
name = output-speaker
priority = 10
[Option Analog Output:Headphones]
name = output-headphones
priority = 9
[Option Analog Output:FP Headphones]
name = output-headphones
priority = 8
[Element Output Select]
enumeration = select
[Option Output Select:Speakers]
name = output-speaker
priority = 10
[Option Output Select:Headphone]
name = output-headphones
priority = 9

mafoelffen@Mikes-ThinkPad-T520:~$ sudo dmesg | grep -i 'audio'
[    0.204539] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[   16.135408] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[   18.001659] snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   19.072361] snd_hda_codec_conexant hdaudioC0D0: CX20590: BIOS auto-probing.
[   19.074821] snd_hda_codec_conexant hdaudioC0D0: autoconfig for CX20590: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   19.074828] snd_hda_codec_conexant hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   19.074832] snd_hda_codec_conexant hdaudioC0D0:    hp_outs=2 (0x1c/0x19/0x0/0x0/0x0)
[   19.074835] snd_hda_codec_conexant hdaudioC0D0:    mono: mono_out=0x0
[   19.074837] snd_hda_codec_conexant hdaudioC0D0:    inputs:
[   19.074840] snd_hda_codec_conexant hdaudioC0D0:      Internal Mic=0x23
[   19.074842] snd_hda_codec_conexant hdaudioC0D0:      Mic=0x1b
[   19.074845] snd_hda_codec_conexant hdaudioC0D0:      Dock Mic=0x1a
[58854.041753] [   2172]  1000  2172   748981      575   258048     1116             0 pulseaudio
[58923.004064] [   2172]  1000  2172   683478      598   253952     1113             0 pulseaudio
[58991.332197] [   2172]  1000  2172   683478      590   253952     1118             0 pulseaudio
[59041.682347] [   2172]  1000  2172   683478      579   253952     1127             0 pulseaudio

mafoelffen@Mikes-ThinkPad-T520:~$ grep . $HOME/.config/pulse/*-default-*
/home/mafoelffen/.config/pulse/23043aec7ab3495381a8778a1b2b4fda-default-sink:alsa_output.usb-Razer_Razer_Kraken_USB-00.analog-stereo
/home/mafoelffen/.config/pulse/23043aec7ab3495381a8778a1b2b4fda-default-source:alsa_input.usb-Razer_Razer_Kraken_USB-00.mono-fallback



```

---

### Post by Mr Fredrick on 2023-03-31
I'm not sure if the following is of any use:

```
~$ pulseaudio -v
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 16.1
I: [pulseaudio] main.c: Page size is 4096 bytes
I: [pulseaudio] main.c: Machine ID is 8c4bc57da9204e318b1e3fe0085bdd3f.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/peter/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-16.1+dfsg1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

```

```

~$  wpctl status
Usage:
  wpctl [OPTION…] COMMAND [COMMAND_OPTIONS] - WirePlumber Control CLI

Commands:
  status 
  get-volume ID
  inspect ID
  set-default ID
  set-volume ID VOL[%][-/+]
  set-mute ID 1|0|toggle
  set-profile ID INDEX
  clear-default [ID]

Help Options:
  -h, --help       Show help options

Pass -h after a command to see command-specific options

peter@peter-desktop:~$ wpctl status
PipeWire 'pipewire-0' [0.3.58, peter@peter-desktop, cookie:3990398253]
 &#9492;&#9472; Clients:
        31. GNOME Shell Volume Control          [0.3.58, peter@peter-desktop, pid:2817]
        33. pipewire                            [0.3.58, peter@peter-desktop, pid:2431]
        34. WirePlumber                         [0.3.58, peter@peter-desktop, pid:2430]
        35. WirePlumber [export]                [0.3.58, peter@peter-desktop, pid:2430]
        42. GNOME Volume Control Media Keys     [0.3.58, peter@peter-desktop, pid:3113]
        47. xdg-desktop-portal                  [0.3.58, peter@peter-desktop, pid:3041]
        53. Firefox                             [0.3.58, peter@peter-desktop, pid:34569]
        54. wpctl                               [0.3.58, peter@peter-desktop, pid:35617]
        55. Firefox                             [0.3.58, peter@peter-desktop, pid:34569]
       194. Mutter                              [0.3.58, peter@peter-desktop, pid:2817]
       222. Terminal                            [0.3.58, peter@peter-desktop, pid:35585]

Audio
 &#9500;&#9472; Devices:
 &#9474;      52. Starship/Matisse HD Audio Controller [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   77. Starship/Matisse HD Audio Controller Analog Stereo [vol: 0.50]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   43. Starship/Matisse HD Audio Controller Analog Stereo [vol: 0.52]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.pci-0000_07_00.1.hdmi-stereo

```

---

### Post by MAFoElffen on 2023-03-31
Good catch 1fallen. I didn't see that he was 22.10. LOL (dang)
```

pactl info

```

---

### Post by Mr Fredrick on 2023-03-31
```
~$ pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 67
Tile Size: 65472
User Name: peter
Host Name: peter-desktop
Server Name: PulseAudio (on PipeWire 0.3.58)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_09_00.4.analog-stereo
Default Source: alsa_input.pci-0000_09_00.4.analog-stereo
Cookie: 485c:30a7
```

Also note, I'm getting lots of messages when I start the system which maybe of use for solving this problem, how can I capture them all for posting here?

---

### Post by MAFoElffen on 2023-03-31
What I usually do is to suggest that people take a picture with their phone (turning the resolution of the camera down), email the picture to themself, then post it as an attachment to a post. 

Is that possible for you?

---

### Post by Mr Fredrick on 2023-03-31
> Is that possible for you? 

I'll try.

---

### Post by Mr Fredrick on 2023-03-31
Attached (I hope) is may attempt at capturing the screen with my phone.

---

### Post by #&amp;thj^% on 2023-03-31
Will you please try:
```
systemctl --user restart pipewire
```
Try sound again
If that does nothing then try:
```
systemctl --user start pipewire-pulse.service
wait ~30 sec
systemctl --user restart pulseaudio.service
```

---

### Post by Mr Fredrick on 2023-03-31
Hi 1fallen,

Followed instructions but no luck.
Note, in the Ubuntu settings app under the Sound tab only my headphones are listed in the the Output Devices not the output device that should be there.

Thanks for your help.

---

### Post by #&amp;thj^% on 2023-03-31
> **Mr Fredrick said:**
> only my headphones are listed in the the Output Devices not the output device that should be there.

Thanks for your help.
Has that always been the case?
also show this please:
```
aplay --list-devices
```

---

### Post by Mr Fredrick on 2023-03-31
```
peter@peter-desktop:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 12: HDMI 6 [HDMI 6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

> Has that always been the case?

Only when sound hasn't worked.

---

### Post by #&amp;thj^% on 2023-03-31
Thank You Sir.
what does this return, paste back please:
```
 systemctl --user --now disable pulseaudio.service pulseaudio.socket
```

---

### Post by Mr Fredrick on 2023-03-31
> systemctl --user --now disable pulseaudio.service pulseaudio.socket

returns nothing.

---

### Post by #&amp;thj^% on 2023-03-31
Good!
one more time:
```
systemctl --user restart pipewire

```

---

### Post by Mr Fredrick on 2023-03-31
> systemctl --user restart pipewire

No luck and now nothing is listed in the Ubuntu settings app Sound Output Devices drop-down.

---

### Post by #&amp;thj^% on 2023-03-31
No problem:
```
systemctl --user start --now pulseaudio.service pulseaudio.socket
systemctl --user enable pulseaudio.service pulseaudio.socket
```
Cross fingers for sound now:
```

systemctl --user restart pipewire

```

---

### Post by Mr Fredrick on 2023-03-31
> systemctl --user start --now pulseaudio.service pulseaudio.socket
systemctl --user enable pulseaudio.service pulseaudio.socket

did above, followed by:

> systemctl --user restart pipewire

no luck

The Ubuntu Settings app once again lists the headphones as Output Devices but not the device it should.

---

### Post by #&amp;thj^% on 2023-03-31
are you able ti file a bug-report for sound?
someone told me this was fixed in kernel-6.xx, I'm not sure I buy it though.
EDIT: Wait I just noticed this>>"Since swapping to the Nvidia 515 driver "
I found that driver version less than usable.
```
apt policy nvidia-driver-525
```

---

### Post by MAFoElffen on 2023-03-31
Are the devices listed in this?
```

alsamixer -V all

```
Please take a screenshot of that and post it as an attachment...

Your errors that you posted are about Snap 'bluez' not starting, which is for Bluetooth file transfers. Unrelated to sound.

---

### Post by #&amp;thj^% on 2023-03-31
> **MAFoElffen said:**
> Are the devices listed in this?
```

alsamixer -V all

```
Please take a screenshot of that and post it as an attachment...

Your errors that you posted are about Snap 'bluez' not starting, which is for Bluetooth file transfers. Unrelated to sound.

Is he not able to select-all copy?
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.2.8 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: PulseAudio                                     F1:  Help               &#9474;
&#9474; Chip: PulseAudio                                     F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5:[All]            F6:  Select sound card  &#9474;
&#9474; Item: Master                                         Esc: Exit               &#9474;
&#9474;                   &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                   &#9474;
&#9474;                   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;                   &#9474;
&#9474;                   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;                   &#9474;
&#9474;                   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;                   &#9474;
&#9474;                   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                   &#9474;
&#9474;                   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                   &#9474;
&#9474;                   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                   &#9474;
&#9474;                   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                   &#9474;
&#9474;                   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                   &#9474;
&#9474;                   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                   &#9474;
&#9474;                   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                   &#9474;
&#9474;                   &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;                   &#9474;
&#9474;                   &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                            &#9474;
&#9474;                   &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;    L    R                  &#9474;
&#9474;                                                     CAPTURE                  &#9474;
&#9474;                  65<>65   65<>65     65       65     68<>68                  &#9474;
&#9474;                < Master > Master   Master   Master  Capture                  &#9474;
&#9474;                  Front     Rear    Center   Woofer                           &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

---

### Post by #&amp;thj^% on 2023-03-31
> **MAFoElffen said:**
> 
Your errors that you posted are about Snap 'bluez' not starting, which is for Bluetooth file transfers. Unrelated to sound.
Bingo>>>by George I think your on to something:
```
sudo apt remove pulseaudio-module-bluetooth
```
Just remove this package and Bluetooth will be handled by PipeWire.
```
apt policy pulseaudio-module-bluetooth
pulseaudio-module-bluetooth:
  Installed: (none)
  Candidate: 1:16.1+dfsg1-2ubuntu3
  Version table:
     1:16.1+dfsg1-2ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages


```

---

### Post by Mr Fredrick on 2023-03-31
```
peter@peter-desktop:~$ apt policy nvidia-driver-525
nvidia-driver-525:
  Installed: (none)
  Candidate: 525.89.02-0ubuntu0.22.10.1
  Version table:
     525.89.02-0ubuntu0.22.10.1 500
        500 http://au.archive.ubuntu.com/ubuntu kinetic-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu kinetic-security/restricted amd64 Packages

```

Sorry, had to go over to the shops for a bit, back now.

---

### Post by #&amp;thj^% on 2023-03-31
Will you up-grade to that version:
also Note post #33

---

### Post by Mr Fredrick on 2023-03-31
Did this:

```
sudo apt remove pulseaudio-module-bluetooth
```

followed by:

```
peter@peter-desktop:~$ apt policy pulseaudio-module-bluetooth
pulseaudio-module-bluetooth:
  Installed: (none)
  Candidate: 1:16.1+dfsg1-1ubuntu3.1
  Version table:
     1:16.1+dfsg1-1ubuntu3.1 500
        500 http://au.archive.ubuntu.com/ubuntu kinetic-updates/universe amd64 Packages
     1:16.1+dfsg1-1ubuntu3 500
        500 http://au.archive.ubuntu.com/ubuntu kinetic/universe amd64 Packages

```

Still no sound, do I have to reboot.

Rebooted anyway, still no sound and only devices listed in the Settings app are the headphones

---

### Post by #&amp;thj^% on 2023-03-31
> **Mr Fredrick said:**
> Did this:

```
sudo apt remove pulseaudio-module-bluetooth
```

followed by:

```
peter@peter-desktop:~$ apt policy pulseaudio-module-bluetooth
pulseaudio-module-bluetooth:
  Installed: (none)
  Candidate: 1:16.1+dfsg1-1ubuntu3.1
  Version table:
     1:16.1+dfsg1-1ubuntu3.1 500
        500 http://au.archive.ubuntu.com/ubuntu kinetic-updates/universe amd64 Packages
     1:16.1+dfsg1-1ubuntu3 500
        500 http://au.archive.ubuntu.com/ubuntu kinetic/universe amd64 Packages

```

Still no sound, do I have to reboot.

Rebooted anyway, still no sound and only devices listed in the Settings app are the headphones
show:
```
nvidia-smi
```
mine:
```
Fri Mar 31 18:18:56 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.41.03              Driver Version: 530.41.03    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1650 Ti      Off| 00000000:01:00.0  On |                  N/A |
| N/A   36C    P5                4W /  N/A|    473MiB /  4096MiB |      1%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      4544      G   /usr/lib/xorg/Xorg                          326MiB |
|    0   N/A  N/A      8590      G   xfwm4                                         2MiB |
|    0   N/A  N/A   1672110      G   /usr/lib/firefox/firefox                    142MiB |
+---------------------------------------------------------------------------------------+

```

---

### Post by Mr Fredrick on 2023-03-31
Requested screenshot attached (I hope).

---

### Post by Mr Fredrick on 2023-03-31
```
peter@peter-desktop:~$ nvidia-smi
Unable to determine the device handle for GPU 0000:07:00.0: Not Found

```

---

### Post by #&amp;thj^% on 2023-03-31
Please do this:
```
sudo apt remove --autoremove nvidia*
```
reboot, and after run:
```
sudo apt install nvidia-driver-525 nvidia-settings
```
and you guessed it, reboot

---

### Post by Mr Fredrick on 2023-03-31
Will do as instructed.

Hope this works, wish me luck, you may not hear from me again if my system bricks up, so thanks anyways.

---

### Post by #&amp;thj^% on 2023-03-31
Good Luck ;)
Don't give up though..

---

### Post by Mr Fredrick on 2023-03-31
The attachment says it all.

Finally success!

A warm thank-you to:
[LIST]
[*]1fallen
[*]MAFoElffen
[*]
[/LIST]
 
MrFredrick

PS. I would mark this as [SOLVED] but I don't know how!

---

### Post by #&amp;thj^% on 2023-03-31
> **Mr Fredrick said:**
> The attachment says it all.

Finally success!

A warm thank-you to:
[LIST]
[*]1fallen
[*]MAFoElffen
[*]
[/LIST]
 
MrFredrick

PS. I would mark this as [SOLVED] but I don't know how!
Great good job.
in your first post, top right corner Thread Tools mark as Solved.
Enjoy

---

