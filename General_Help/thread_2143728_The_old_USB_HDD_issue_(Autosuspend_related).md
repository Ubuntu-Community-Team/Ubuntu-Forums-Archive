---
title: "The old USB HDD issue (Autosuspend related?)"
date: 2013-05-09
forum: General Help
---

### Post by Crogge on 2013-05-09
[TABLE="class: topic"]
[TR]
[TD="class: post, bgcolor: #F8F6F1"]First of all the basic system informations:

[LIST]
[*]Ubuntu 12.04.2 LTS 
[*]Linux futroli 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux 
[*]WD My Passport USB 3.0 HDD 
[/LIST]
[/TD]
[/TR]
[/TABLE]

I heard this morning a strange clicking noise from my USB HDD and found the following logs *(Device was turned on around 2 days without problems)*:
```
May  9 05:39:55 futroli kernel: [171669.512028] usb 1-8: reset high-speed USB device number 2 using ehci_hcd
May  9 05:39:55 futroli kernel: [171669.624055] usb 1-8: device descriptor read/64, error -32
May  9 05:39:55 futroli kernel: [171669.840025] usb 1-8: device descriptor read/64, error -32
May  9 05:39:55 futroli kernel: [171670.056021] usb 1-8: reset high-speed USB device number 2 using ehci_hcd
May  9 05:39:55 futroli kernel: [171670.168018] usb 1-8: device descriptor read/64, error -32
May  9 05:39:56 futroli kernel: [171670.384019] usb 1-8: device descriptor read/64, error -32
May  9 05:39:56 futroli kernel: [171670.600063] usb 1-8: reset high-speed USB device number 2 using ehci_hcd
May  9 05:39:56 futroli kernel: [171670.620635] usb 1-8: device descriptor read/8, error -32
May  9 05:39:56 futroli kernel: [171670.740648] usb 1-8: device descriptor read/8, error -32
May  9 05:39:56 futroli kernel: [171670.956022] usb 1-8: reset high-speed USB device number 2 using ehci_hcd
May  9 05:39:56 futroli kernel: [171670.976681] usb 1-8: device descriptor read/8, error -32
May  9 05:39:56 futroli kernel: [171671.096573] usb 1-8: device descriptor read/8, error -32
May  9 05:39:56 futroli kernel: [171671.200057] usb 1-8: USB disconnect, device number 2
May  9 05:39:56 futroli kernel: [171671.212054] sd 0:0:0:0: [sdb] Unhandled error code
May  9 05:39:56 futroli kernel: [171671.212065] sd 0:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
May  9 05:39:56 futroli kernel: [171671.212074] sd 0:0:0:0: [sdb] CDB: Write(10): 2a 00 2b e8 0b 20 00 00 08 00
May  9 05:39:56 futroli kernel: [171671.212093] end_request: I/O error, dev sdb, sector 736627488
May  9 05:39:56 futroli kernel: [171671.214235] Buffer I/O error on device sdb1, logical block 92078180
May  9 05:39:56 futroli kernel: [171671.216330] lost page write due to I/O error on sdb1
May  9 05:39:57 futroli kernel: [171671.652042] usb 1-8: new high-speed USB device number 3 using ehci_hcd
May  9 05:39:57 futroli kernel: [171671.764022] usb 1-8: device descriptor read/64, error -32
May  9 05:39:57 futroli kernel: [171671.980024] usb 1-8: device descriptor read/64, error -32
May  9 05:39:57 futroli kernel: [171672.196026] usb 1-8: new high-speed USB device number 4 using ehci_hcd
May  9 05:39:58 futroli kernel: [171672.308026] usb 1-8: device descriptor read/64, error -32
May  9 05:39:58 futroli kernel: [171672.524027] usb 1-8: device descriptor read/64, error -32
May  9 05:39:58 futroli kernel: [171672.740023] usb 1-8: new high-speed USB device number 5 using ehci_hcd
May  9 05:39:58 futroli kernel: [171672.760675] usb 1-8: device descriptor read/8, error -32
May  9 05:39:58 futroli kernel: [171672.880564] usb 1-8: device descriptor read/8, error -32
May  9 05:39:58 futroli kernel: [171673.096048] usb 1-8: new high-speed USB device number 6 using ehci_hcd
May  9 05:39:58 futroli kernel: [171673.116596] usb 1-8: device descriptor read/8, error -32
May  9 05:39:59 futroli kernel: [171673.237407] usb 1-8: device descriptor read/8, error -32
May  9 05:39:59 futroli kernel: [171673.340054] hub 1-0:1.0: unable to enumerate USB device on port 8
May  9 05:39:59 futroli kernel: [171673.672032] usb 5-2: new full-speed USB device number 2 using ohci_hcd
May  9 05:39:59 futroli kernel: [171673.812021] usb 5-2: device descriptor read/64, error -32
May  9 05:39:59 futroli kernel: [171674.056019] usb 5-2: device descriptor read/64, error -32
May  9 05:40:00 futroli kernel: [171674.296023] usb 5-2: new full-speed USB device number 3 using ohci_hcd
May  9 05:40:00 futroli kernel: [171674.436031] usb 5-2: device descriptor read/64, error -32
May  9 05:40:00 futroli kernel: [171674.680039] usb 5-2: device descriptor read/64, error -32
May  9 05:40:00 futroli kernel: [171674.920020] usb 5-2: new full-speed USB device number 4 using ohci_hcd
May  9 05:40:00 futroli kernel: [171674.945055] usb 5-2: device descriptor read/8, error -32
May  9 05:40:00 futroli kernel: [171675.069053] usb 5-2: device descriptor read/8, error -32
May  9 05:40:01 futroli kernel: [171675.308022] usb 5-2: new full-speed USB device number 5 using ohci_hcd
May  9 05:40:01 futroli kernel: [171675.333054] usb 5-2: device descriptor read/8, error -32
May  9 05:40:01 futroli kernel: [171675.457057] usb 5-2: device descriptor read/8, error -32
May  9 05:40:01 futroli kernel: [171675.560071] hub 5-0:1.0: unable to enumerate USB device on port 2
May  9 05:41:04 futroli smbd[636]: [2013/05/09 05:41:04.413325,  0] printing/print_standard.c:68(std_pcap_cache_reload)
May  9 05:41:04 futroli smbd[636]:   Unable to open printcap file /etc/printcap for read!
May  9 05:41:07 futroli kernel: [171741.650714] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=23021096, block=92078180
May  9 05:41:07 futroli kernel: [171741.652608] Aborting journal on device sdb1.
May  9 05:41:07 futroli kernel: [171741.655409] Buffer I/O error on device sdb1, logical block 122028546
May  9 05:41:07 futroli kernel: [171741.656590] lost page write due to I/O error on sdb1
May  9 05:41:07 futroli kernel: [171741.657620] JBD: I/O error detected when updating journal superblock for sdb1.
May  9 05:41:07 futroli kernel: [171741.659496] EXT3-fs (sdb1): error: remounting filesystem read-only
May  9 05:41:07 futroli kernel: [171741.662166] Buffer I/O error on device sdb1, logical block 0
May  9 05:41:07 futroli kernel: [171741.664053] lost page write due to I/O error on sdb1
May  9 05:41:07 futroli kernel: [171741.664389] EXT3-fs (sdb1): I/O error while writing superblock
May  9 05:41:07 futroli kernel: [171741.666276] EXT3-fs (sdb1): error in ext3_reserve_inode_write: IO failure
May  9 05:41:07 futroli kernel: [171741.668203] EXT3-fs (sdb1): error in ext3_dirty_inode: IO failure
May  9 06:49:47 futroli kernel: [175862.224780] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #53388534 offset 0
May  9 06:49:48 futroli kernel: [175862.913208] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
May  9 06:49:48 futroli CRON[4769]: (CRON) info (No MTA installed, discarding output)
```

I didn't had any issue like that with Debian *(2.6 kernel)* and I noticed that there exist a lot of threads about this kind of issue in relation with Ubuntu.

Its strange though that the "USBCORE" module isn't loaded on boot nor there is any message about it. However, all USB devices are working fine on boot apart from the USB HDD issue after a few hours/days.

**Is it recommended to load the USBCORE module on boot or is there any other module which replaced it? Or is the USBCORE module implemented inside the kernel?**

How can I Set this parameters automatically on boot?

echo Y > /sys/module/usbcore/parameters/old_scheme_first
echo 5 >/sys/module/usbcore/parameters/autosuspend

I tried ways descried on [http://lwn.net/Articles/253587/](http://lwn.net/Articles/253587/) but Ubuntu is ignoring the entries in "/etc/modules" and keeps using "2" which is a very low value in my point of view.

Thank you in advance for your help :)

---

### Post by Crogge on 2013-05-11
Bump.

---

