---
title: "package installer error"
date: 2016-06-06
forum: General Help
---

### Post by ali61 on 2016-06-06
[ATTACH=CONFIG]269456[/ATTACH]what is the problem

---

### Post by howefield on 2016-06-06
The 32 bit version of the Chrome web browser is no longer supported.

You'd be better of with Firefox or another browser, Chromium or Opera for example.

---

### Post by ali61 on 2016-06-06
but this happens in other files as well[ATTACH=CONFIG]269457[/ATTACH]

---

### Post by kansasnoob on 2016-06-06
Please post the output of:

```
lsb_release -a
```

---

### Post by ali61 on 2016-06-06
ali@ali-X101CH:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

---

### Post by ventrical on 2016-06-07
and,

```

uname -a

```

thanks.

edit

could you also put this code into terminal and report:

```

lspci

```

---

### Post by ali61 on 2016-06-25
ali@ali-X101CH:~$ uname -a
Linux ali-X101CH 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:15 UTC 2016 i686 i686 i686 GNU/Linux


...................................................................................................................................................................................
```
ali@ali-X101CH:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)
```

---

