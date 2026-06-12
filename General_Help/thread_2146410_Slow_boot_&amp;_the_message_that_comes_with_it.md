---
title: "Slow boot &amp; the message that comes with it"
date: 2013-05-18
forum: General Help
---

### Post by sunfromhere on 2013-05-18
Hello! Ubuntu is 12.04, PC is Eee PC (dual core Atom with HT, 1.4 GHZ, 2GB RAM).

I have this hole in my boot time, shown in dmesg:

[     8.460923] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   21.503622] ADDRCONF(NETDEV_UP): eth0: link is not ready

Total boot time is 28 seconds, which I don't mind, I just wonder what this part means: EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null), and why does it make a 10 seconds pause in the boot. I googled it, but didn't get any smarter. :confused:

Thanks!

---

### Post by pqwoerituytrueiwoq on 2013-05-18
i was able to make that shorter by using uefi boot in my bios, using 13.04 here
the second line you posted is the real issue, looks to be ~12 seconds of your boot time
try disabling ipv6 and see if it boot faster, use [FONT=courier new]ipv6.disable=1[/FONT] in your kernel boot line and see if it boots faster

---

### Post by sunfromhere on 2013-05-18
Ipv6 is disabled:

cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1

---

### Post by pqwoerituytrueiwoq on 2013-05-18
when i boot using that, the command does this
```
~$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
0
```

---

### Post by sunfromhere on 2013-05-18
I changed it*, now it is also 0. Now I get two holes:

[    7.999398] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   20.872102] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   27.573025] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.784274] wlan0: no IPv6 routers present


*in /etc/sysctl.conf

---

### Post by pqwoerituytrueiwoq on 2013-05-18
can yuo post the output of [FONT=courier new]lspci[/FONT]

---

### Post by sunfromhere on 2013-05-19
Here it is:

```
00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
```

---

