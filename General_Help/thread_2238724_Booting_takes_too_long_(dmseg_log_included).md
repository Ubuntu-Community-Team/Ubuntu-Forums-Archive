---
title: "Booting takes too long (dmseg log included)"
date: 2014-08-09
forum: General Help
---

### Post by ceciliasp on 2014-08-09
Hi, 
I have a ASUS SC400 Intel® Core™ i5-3317U CPU @ 1.70GHz × 4 64-b laptop and it used to boot very fast (normally it would take no more than 10-20 seconds)
It's been a while since it started taking too long untill I could see my desktop-
I ran the  gksudo gedit /var/log/dmesg command and I see a couple hops in time that draw my attention:

The first one is about 2 seconds
```
[    2.775443] Switched to clocksource tsc
[    6.957949] Adding 4077564k swap on /dev/sda3.  Priority:-1 extents:1 across:4077564k FS
[    8.024899] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.220212] systemd-udevd[301]: starting version 204
[    8.940934] lp: driver loaded but no devices found
[    8.982981] ppdev: user-space parallel port driver
```

A warning (?):
```
[   10.704831] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   12.471203] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPIS 1 (20131115/utaddress-251)
[   12.471211] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 2 (20131115/utaddress-251)
[   12.471216] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.471220] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   12.471225] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
[   12.471228] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.471230] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   12.471234] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
```

A 4 seconds hop

```
[   15.355839] hid-multitouch 0003:03EB:8807.0001: input,hiddev0,hidraw0: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:1a.0-1.3/input0
[   15.355933] hid-generic 0003:03EB:8807.0002: hiddev0,hidraw1: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:1a.0-1.3/input1
[   19.318705] type=1400 audit(1407612259.864:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=507 comm="apparmor_parser"
[   19.318714] type=1400 audit(1407612259.864:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=507 comm="apparmor_parser"
[   19.318721] type=1400 audit(1407612259.864:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=507 comm="apparmor_parser"
[   19.318769] type=1400 audit(1407612259.864:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=433 comm="apparmor_parser"
[   19.318778] type=1400 audit(1407612259.864:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=433 comm="apparmor_parser"
[   19.318783] type=1400 audit(1407612259.864:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
[   19.318791] type=1400 audit(1407612259.864:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=552 comm="apparmor_parser"
[   19.318797] type=1400 audit(1407612259.864:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=552 comm="apparmor_parser"
[   19.318803] type=1400 audit(1407612259.864:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=552 comm="apparmor_parser"
[   19.319185] type=1400 audit(1407612259.868:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=507 comm="apparmor_parser"
```

Strange that bluetooth is initialized since I've disabled it
```
[   20.164847] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.170791] init: failsafe main process (683) killed by TERM signal
[   27.951636] Bluetooth: Core ver 2.17
[   27.951653] NET: Registered protocol family 31
[   27.951654] Bluetooth: HCI device and connection manager initialized
[   27.951662] Bluetooth: HCI socket layer initialized
[   27.951663] Bluetooth: L2CAP socket layer initialized
[   27.951666] Bluetooth: SCO socket layer initialized
[   28.182835] Bluetooth: RFCOMM TTY layer initialized
[   28.182849] Bluetooth: RFCOMM socket layer initialized
[   28.182856] Bluetooth: RFCOMM ver 1.11
[   28.572014] init: avahi-cups-reload main process (925) terminated with status 1
[   28.708958] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.708962] Bluetooth: BNEP filters: protocol multicast
[   28.708972] Bluetooth: BNEP socket layer initialized
```

A ten second hop!!!
```
[   29.640425] type=1400 audit(1407612270.184:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=855 comm="apparmor_parser"
[   29.640432] type=1400 audit(1407612270.184:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=855 comm="apparmor_parser"
[   29.640836] type=1400 audit(1407612270.184:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=855 comm="apparmor_parser"
[   37.956807] type=1400 audit(1407612278.496:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1017 comm="apparmor_parser"
[   37.956815] type=1400 audit(1407612278.496:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1017 comm="apparmor_parser"
[   37.956818] type=1400 audit(1407612278.496:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1017 comm="apparmor_parser"
[   37.957199] type=1400 audit(1407612278.496:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1017 comm="apparmor_parser"
[   37.957202] type=1400 audit(1407612278.496:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1017 comm="apparmor_parser"
[   37.957399] type=1400 audit(1407612278.496:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1017 comm="apparmor_parser"
[   38.001595] init: samba-ad-dc main process (952) terminated with status 1
[   38.236889] type=1400 audit(1407612278.776:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=1018 comm="apparmor_parser"
[   38.639654] type=1400 audit(1407612279.176:30): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1015 comm="apparmor_parser"
[   38.639664] type=1400 audit(1407612279.176:31): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1015 comm="apparmor_parser"
[   38.640141] type=1400 audit(1407612279.180:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1015 comm="apparmor_parser"
[   40.422726] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.425763] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.470940] alx 0000:03:00.0: irq 47 for MSI/MSI-X
[   40.471020] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.471334] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
```


Anyone could give me any advice on any of this entries?

Txs.

---

