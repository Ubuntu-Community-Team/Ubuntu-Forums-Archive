---
title: "Computer fails to wake up after suspend"
date: 2014-02-24
forum: General Help
---

### Post by haydemon on 2014-02-24
I'm having a problem after installing Ubuntu 13.10 in my Toshiba Satellite L455 laptop. It fails to wake up after hibernation/suspension. I have to do a hard bootup every time I come back to it after having left it for an extended period, either overnight, or throughout the day when it "goes to sleep" after a period of inactivity. I'm using Gnome Classic, but this happens regardless of the DM I use. This is the output after running [B]sudo lshw -C network:
[/B]> [INDENT] *-network               [/INDENT]
[INDENT]       description: Ethernet interface[/INDENT]
[INDENT]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/INDENT]
[INDENT]       vendor: Realtek Semiconductor Co., Ltd.[/INDENT]
[INDENT]       physical id: 0[/INDENT]
[INDENT]       bus info: pci@0000:0e:00.0[/INDENT]
[INDENT]       logical name: eth0[/INDENT]
[INDENT]       version: 02[/INDENT]
[INDENT]       serial: 00:26:22:47:7d:1c[/INDENT]
[INDENT]       size: 10Mbit/s[/INDENT]
[INDENT]       capacity: 100Mbit/s[/INDENT]
[INDENT]       width: 64 bits[/INDENT]
[INDENT]       clock: 33MHz[/INDENT]
[INDENT]       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/INDENT]
[INDENT]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/INDENT]
[INDENT]       resources: irq:44 ioport:3000(size=256) memory:f2010000-f2010fff memory:f2000000-f200ffff memory:f2020000-f203ffff[/INDENT]
[INDENT]  *-network[/INDENT]
[INDENT]       description: Wireless interface[/INDENT]
[INDENT]       physical id: 2[/INDENT]
[INDENT]       bus info: usb@1:2[/INDENT]
[INDENT]       logical name: wlan0[/INDENT]
[INDENT]       serial: 70:1a:04:70:9b:92[/INDENT]
[INDENT]       capabilities: ethernet physical wireless[/INDENT]
[INDENT]       configuration: broadcast=yes driver=rtl8187 driverversion=3.11.0-18-generic firmware=N/A ip=192.168.1.69 link=yes multicast=yes wireless=IEEE 802.11bg

[/INDENT]
Thanks for any help you can provide.

---

### Post by tgalati4 on 2014-02-24
Open a terminal and post any errors that you find in:

```
less /var/log/pm-powersave.log
less /var/log/pm-suspend.log
```

---

### Post by haydemon on 2014-02-24
Still running process 1, so far no errors; process 2, no errors, except some are marked "not applicable." Are these considered errors? Or would you rather see the entire output?Please clarify. Thx

---

