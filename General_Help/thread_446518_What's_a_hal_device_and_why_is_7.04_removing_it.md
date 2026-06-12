---
title: "What's a hal device and why is 7.04 removing it"
date: 2007-05-17
forum: General Help
---

### Post by tictacman on 2007-05-17
In my syslog I've got an entry indicating removal of hal device:

May 16 08:16:54 ubuntu kernel: [ 2915.682332] sd 4:0:0:0: rejecting I/O to offline device
May 16 08:16:54 ubuntu kernel: [ 2915.683294] sd 4:0:0:0: rejecting I/O to offline device
May 16 08:16:54 ubuntu kernel: [ 2915.683300] printk: 48 messages suppressed.
May 16 08:16:54 ubuntu kernel: [ 2915.683303] Buffer I/O error on device sdc2, logical block 23381
May 16 08:16:54 ubuntu kernel: [ 2915.683305] lost page write due to I/O error on sdc2
May 16 08:17:01 ubuntu /USR/SBIN/CRON[7105]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 16 08:17:54 ubuntu kernel: [ 2953.072655] usb 8-2: USB disconnect, address 3
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.071222] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.090902] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.183568] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.229132] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.283527] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.290100] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.294672] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.324304] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:17:54 ubuntu NetworkManager: <debug info>^I[1179299874.369729] nm_hal_device_removed (): Device removed (hal udi i$
May 16 08:41:32 ubuntu -- MARK --
May 16 09:01:32 ubuntu -- MARK --

Anybody know what's happening here? Could it be my ipod that failed to work yesterday.

---

### Post by MoLE on 2007-05-23
Seems to be Network Manager complaining that one of the devices it manages was removed.  My guess is that you could see that when toggling the on/off switch for your wireless card on a laptop?

---

