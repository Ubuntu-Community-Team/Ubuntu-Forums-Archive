---
title: "Ubuntu isn't detecting MP3 Player"
date: 2013-02-08
forum: General Help
---

### Post by danielmrg on 2013-02-08
Hey,

I am trying to run an old Creative Jukebox player and it seems like Ubuntu is not recognizing it. it is plugged by USB cable, and unlike other players i plug - Ubuntu is not responding at all, not detecting it (as it seems by the Disk Utility).

I am using Ubuntu 12.04 on PC. The player I am trying to plug is a Creative NOMAD Jukebox Zen Xtra.

In case it can help, this is my DMESG (dmesg|tail -n 20)

> [   22.936835] type=1400 audit(1360345287.245:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=887 comm="apparmor_parser"
[   22.937499] type=1400 audit(1360345287.245:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=887 comm="apparmor_parser"
[   22.942300] type=1400 audit(1360345287.249:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=889 comm="apparmor_parser"
[   22.942916] type=1400 audit(1360345287.249:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=889 comm="apparmor_parser"
[   23.031084] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9
[   23.092175] type=1400 audit(1360345287.401:21): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=890 comm="apparmor_parser"
[   23.092510] type=1400 audit(1360345287.401:22): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=890 comm="apparmor_parser"
[   23.101471] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.102092] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.652288] init: plymouth-stop pre-start process (1173) terminated with status 1
[   31.832308] wlan0: authenticate with 00:21:04:4a:0a:62 (try 1)
[   31.844715] wlan0: authenticated
[   31.848476] wlan0: associate with 00:21:04:4a:0a:62 (try 1)
[   31.942481] wlan0: RX AssocResp from 00:21:04:4a:0a:62 (capab=0x431 status=0 aid=3)
[   31.942486] wlan0: associated
[   31.966609] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.288068] wlan0: no IPv6 routers present
[  103.104102] usb 2-1: new high-speed USB device number 4 using ehci_hcd
[  139.350264] usb 2-1: USB disconnect, device number 4
[  555.752093] usb 2-1: new high-speed USB device number 5 using ehci_hcd


I will be great full if someone could help me with that.

Thanks,
Daniel

---

