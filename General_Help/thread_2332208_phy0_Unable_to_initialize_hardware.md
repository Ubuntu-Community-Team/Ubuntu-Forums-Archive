---
title: "phy0: Unable to initialize hardware"
date: 2016-07-29
forum: General Help
---

### Post by mavik1 on 2016-07-29
Hello,

# dmesg | grep ath  displays

```
[    2.080299] Loaded X.509 cert 'Magrathea: Glacier signing key: 77d70e1df42996dc92b01d759d3e8562ea32a1c7'
[   22.097509] usbcore: registered new interface driver ath3k
[   22.851245] ath9k 0000:0c:00.0: enabling device (0000 -> 0002)
[   23.035406] ath: phy0: Couldn't reset chip
[   23.035410] ath: phy0: Unable to initialize hardware; initialization status: -5
[   23.035418] ath9k 0000:0c:00.0: Failed to initialize device
[   23.084220] ath9k: probe of 0000:0c:00.0 failed with error -5

```

lspci -nnk | grep -iA2 atheros

```
0c:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Dell Wireless 1702 802.11bgn Half-size Mini PCIe Card [AR9002WB-1NGCD] [1028:0205]
0f:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev ff)

```

How to slove this.

Thank You

---

