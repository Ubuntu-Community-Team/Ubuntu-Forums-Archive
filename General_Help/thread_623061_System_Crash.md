---
title: "System Crash"
date: 2007-11-25
forum: General Help
---

### Post by tezzaa on 2007-11-25
Hi my system just crashed when I inserted a DVD to view with Movie Player.

Here is the sys log, any ideas what caused the crash.  Also what is the best Movie Player to use in Ubuntu Gutsy 7.10.

[B]Nov 25 18:10:17 terry-desktop NetworkManager: <debug> [1196014217.898345] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_WHAT_THE_BLEEP_1'). 
Nov 25 18:10:20 terry-desktop kernel: [13838.229167] UDF-fs: Partition marked readonly; forcing readonly mount
Nov 25 18:10:21 terry-desktop kernel: [13838.356246] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'WHAT_THE_BLEEP_1', timestamp 2005/08/31 11:01 (1000)
Nov 25 18:10:23 terry-desktop kernel: [13841.125882] end_request: I/O error, dev sr0, sector 1668
Nov 25 18:10:23 terry-desktop kernel: [13841.125898] Buffer I/O error on device sr0, logical block 417
Nov 25 18:10:23 terry-desktop kernel: [13841.125910] Buffer I/O error on device sr0, logical block 418
Nov 25 18:10:23 terry-desktop kernel: [13841.125914] Buffer I/O error on device sr0, logical block 419
Nov 25 18:10:23 terry-desktop kernel: [13841.125918] Buffer I/O error on device sr0, logical block 420
Nov 25 18:10:23 terry-desktop kernel: [13841.125922] Buffer I/O error on device sr0, logical block 421
Nov 25 18:10:23 terry-desktop kernel: [13841.125926] Buffer I/O error on device sr0, logical block 422
Nov 25 18:10:23 terry-desktop kernel: [13841.125930] Buffer I/O error on device sr0, logical block 423
Nov 25 18:10:23 terry-desktop kernel: [13841.125934] Buffer I/O error on device sr0, logical block 424
Nov 25 18:10:23 terry-desktop kernel: [13841.125938] Buffer I/O error on device sr0, logical block 425
Nov 25 18:10:23 terry-desktop kernel: [13841.125942] Buffer I/O error on device sr0, logical block 426
Nov 25 18:10:23 terry-desktop kernel: [13841.199338] end_request: I/O error, dev sr0, sector 14320
Nov 25 18:10:23 terry-desktop kernel: [13841.266207] end_request: I/O error, dev sr0, sector 14324
Nov 25 18:10:24 terry-desktop kernel: [13841.327193] end_request: I/O error, dev sr0, sector 14320
Nov 25 18:10:24 terry-desktop kernel: [13841.387205] end_request: I/O error, dev sr0, sector 14320
Nov 25 18:17:01 terry-desktop /USR/SBIN/CRON[9963]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 25 18:30:23 terry-desktop NetworkManager: <debug> [1196015423.972693] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_WHAT_THE_BLEEP_1'). 
Nov 25 18:30:38 terry-desktop NetworkManager: <debug> [1196015438.040001] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_WHAT_THE_BLEEP_1'). 
Nov 25 18:30:38 terry-desktop kernel: [15055.222765] UDF-fs: Partition marked readonly; forcing readonly mount
Nov 25 18:30:38 terry-desktop kernel: [15055.474424] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'WHAT_THE_BLEEP_1', timestamp 2005/08/31 11:01 (1000)
Nov 25 18:30:42 terry-desktop kernel: [15058.654047] end_request: I/O error, dev sr0, sector 1604
Nov 25 18:30:42 terry-desktop kernel: [15058.654060] printk: 89 messages suppressed.
Nov 25 18:30:42 terry-desktop kernel: [15058.654065] Buffer I/O error on device sr0, logical block 401
Nov 25 18:30:42 terry-desktop kernel: [15058.654078] Buffer I/O error on device sr0, logical block 402
Nov 25 18:30:42 terry-desktop kernel: [15058.654082] Buffer I/O error on device sr0, logical block 403
Nov 25 18:30:42 terry-desktop kernel: [15058.654086] Buffer I/O error on device sr0, logical block 404
Nov 25 18:30:42 terry-desktop kernel: [15058.654090] Buffer I/O error on device sr0, logical block 405
Nov 25 18:30:42 terry-desktop kernel: [15058.654094] Buffer I/O error on device sr0, logical block 406
Nov 25 18:30:42 terry-desktop kernel: [15058.654098] Buffer I/O error on device sr0, logical block 407
Nov 25 18:30:42 terry-desktop kernel: [15058.654102] Buffer I/O error on device sr0, logical block 408
Nov 25 18:30:42 terry-desktop kernel: [15058.654106] Buffer I/O error on device sr0, logical block 409
Nov 25 18:30:42 terry-desktop kernel: [15058.654110] Buffer I/O error on device sr0, logical block 410
Nov 25 18:33:33 terry-desktop gdm[5014]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 25 18:34:02 terry-desktop hcid[4964]: Default passkey agent (:1.71, /org/bluez/passkey) registered
Nov 25 18:34:02 terry-desktop hcid[4964]: Default authorization agent (:1.71, /org/bluez/auth) registered
Nov 25 18:34:05 terry-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 25 18:34:05 terry-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. [/B]

Thanks

Terry (2 week old newbie)

---

