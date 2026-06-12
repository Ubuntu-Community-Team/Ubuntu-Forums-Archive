---
title: "battery discharging even when on standby"
date: 2012-11-17
forum: General Help
---

### Post by abelito8 on 2012-11-17
Hi, after my upgrade to 12.04 my asus keeps on discharging its battery even when on standby. When I had 11.10 I could close the lid and re-open it after a few hours. If I do this now the next time I open the lid the laptop will simply restart (as it had been switched off) and the battery will be almost empty

---

### Post by idoitprone on 2012-11-17
> **abelito8 said:**
> Hi, after my upgrade to 12.04 my asus keeps on discharging its battery even when on standby. When I had 11.10 I could close the lid and re-open it after a few hours. If I do this now the next time I open the lid the laptop will simply restart (as it had been switched off) and the battery will be almost empty

```
lspci -nnk
```
let see your system

it is normal to discharge on standby because the computer is still using power to maintain ram.

---

### Post by abelito8 on 2012-11-17
thanks, here we go

lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1b12]
00:01.0 PCI bridge [0604]: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx) [1043:9602]
    Kernel modules: shpchp
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1117]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel driver in use: ohci_hcd
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel driver in use: ehci_hcd
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ce]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1df7]
    Kernel driver in use: ohci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics] [1002:9612]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1b12]
    Kernel driver in use: radeon
    Kernel modules: radeon
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: AzureWave Device [1a3b:1107]
    Kernel driver in use: rtl8192se
    Kernel modules: rtl8192se
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8304]
    Kernel driver in use: atl1c
    Kernel modules: atl1c

---

### Post by idoitprone on 2012-11-17
ACk, an old ati card

I do not know what to do because both graphic drivers stink 

Open source and binary blobs are bad

---

### Post by abelito8 on 2012-11-17
I see, all too bad, but if I decide to go on with my life :) is there anything I can do? It worked fine until I upgraded to 12.04...

---

### Post by offgridguy on 2012-11-17
> **idoitprone said:**
> ```
lspci -nnk
```let see your system

it is normal to discharge on standby because the computer is still using power to maintain ram.


Thank you for this nugget. {code}

---

### Post by abelito8 on 2012-11-18
ok, thanks, Did this also
 it's normal that it gets discharged but it's too fast now

---

