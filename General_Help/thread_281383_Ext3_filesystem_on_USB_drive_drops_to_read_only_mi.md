---
title: "Ext3 filesystem on USB drive drops to read only mid-write"
date: 2006-10-21
forum: General Help
---

### Post by themightychris on 2006-10-21
Alright, this is starting to drive me insain, I can't get through more than a  couple hundred megs without it happening.

I have a 250 GB usb hard drive with a 100 GB ext3 partition which ubuntu picks up and mounts just fine.  Almost every time I copy files to the drive though, usually after a hundered megs or so, the write will suddenly fail saying "Read-only file system" and the partition will now be indeed read only.  I have to unmount and remount the drive to make it writable again, but it will drop to read only again after doing some writing.

Any suggestions? Is this a physically bad hard drive?


Example command output:
```

chris@Chris-workstation:~/Videos/Lost$ cp * /media/MediaDrive/Shows/Lost/
cp: writing `/media/MediaDrive/Shows/Lost/Lost.S03.E02.avi': Read-only file syst em
cp: cannot create regular file `/media/MediaDrive/Shows/Lost/Lost.S03.E03.avi': Read-only file system

```

Log data:
```

chris@Chris-workstation:~/Videos/Lost$ tail -n 50 /var/log/messages
Oct 21 00:19:29 localhost kernel: [22043.498334] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:30 localhost kernel: [22044.581748] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:30 localhost kernel: [22044.690471] sd 7:0:0:0: SCSI error: return code = 0x70000
Oct 21 00:19:30 localhost kernel: [22044.690476] end_request: I/O error, dev sdc, sector 2109171
Oct 21 00:19:31 localhost kernel: [22045.637061] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:32 localhost kernel: [22046.704350] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:33 localhost kernel: [22047.775652] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:34 localhost kernel: [22048.842954] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:35 localhost kernel: [22049.914241] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:35 localhost kernel: [22050.023082] sd 7:0:0:0: SCSI error: return code = 0x70000
Oct 21 00:19:35 localhost kernel: [22050.023088] end_request: I/O error, dev sdc, sector 2109179
Oct 21 00:19:36 localhost kernel: [22050.981535] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:37 localhost kernel: [22052.052823] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:39 localhost kernel: [22053.120127] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:40 localhost kernel: [22054.191413] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:41 localhost kernel: [22055.258833] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:41 localhost kernel: [22055.367554] sd 7:0:0:0: SCSI error: return code = 0x70000
Oct 21 00:19:41 localhost kernel: [22055.367558] end_request: I/O error, dev sdc, sector 2109187
Oct 21 00:19:42 localhost kernel: [22056.330118] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:43 localhost kernel: [22057.397404] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:44 localhost kernel: [22058.468692] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:45 localhost kernel: [22059.535989] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:46 localhost kernel: [22060.607271] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:46 localhost kernel: [22060.716178] sd 7:0:0:0: SCSI error: return code = 0x70000
Oct 21 00:19:46 localhost kernel: [22060.716183] end_request: I/O error, dev sdc, sector 2109195
Oct 21 00:19:47 localhost kernel: [22061.674704] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:48 localhost kernel: [22062.745862] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:49 localhost kernel: [22063.813278] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:50 localhost kernel: [22064.884434] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:51 localhost kernel: [22065.951726] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:52 localhost kernel: [22066.060571] sd 7:0:0:0: SCSI error: return code = 0x70000
Oct 21 00:19:52 localhost kernel: [22066.060576] end_request: I/O error, dev sdc, sector 2109203
Oct 21 00:19:52 localhost kernel: [22067.023139] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:54 localhost kernel: [22068.090430] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:55 localhost kernel: [22069.161708] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:56 localhost kernel: [22070.228999] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:57 localhost kernel: [22071.312279] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:57 localhost kernel: [22071.421123] sd 7:0:0:0: SCSI error: return code = 0x70000
Oct 21 00:19:57 localhost kernel: [22071.421127] end_request: I/O error, dev sdc, sector 2109211
Oct 21 00:19:58 localhost kernel: [22072.367575] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:19:59 localhost kernel: [22073.450854] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:20:00 localhost kernel: [22074.506150] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:20:01 localhost kernel: [22075.589424] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:20:02 localhost kernel: [22076.644861] usb 1-4.1: reset high speed USB device using ehci_hcd and address 6
Oct 21 00:20:02 localhost kernel: [22076.737591] sd 7:0:0:0: SCSI error: return code = 0x70000
Oct 21 00:20:02 localhost kernel: [22076.737595] end_request: I/O error, dev sdc, sector 2109219
Oct 21 00:20:08 localhost kernel: [22082.099586] __journal_remove_journal_head: freeing b_committed_data
Oct 21 00:20:08 localhost kernel: [22082.099623] __journal_remove_journal_head: freeing b_committed_data
Oct 21 00:20:08 localhost kernel: [22082.099636] __journal_remove_journal_head: freeing b_committed_data
Oct 21 00:20:08 localhost kernel: [22082.099641] __journal_remove_journal_head: freeing b_committed_data

```

---

### Post by jefrat72 on 2006-11-01
Figure it out?  I have the same thing, getting on my nerves too.

---

### Post by themightychris on 2006-11-04
nope, it's totally fine though with small files here and there.  It is only when i try to move a lot on it all at once that it dies, is this the behavior you experience too?

---

### Post by marmel on 2006-11-05
Hi guys,
Same problem here...
I am in panic! :shock:

> Nov  5 02:10:11 saturn kernel: [17199119.808000] EXT3 FS on sdb5, internal journal
Nov  5 02:10:11 saturn kernel: [17199119.808000] EXT3-fs: mounted filesystem with ordered data mode.
Nov  5 02:14:24 saturn kernel: [17199372.460000] usb 5-2: reset high speed USB device using ehci_hcd and address 4
Nov  5 02:16:24 saturn kernel: [17199492.864000] __journal_remove_journal_head:
freeing b_committed_data
Nov  5 02:22:53 saturn kernel: [17199882.352000] __journal_remove_journal_head:
freeing b_committed_data
Nov  5 02:23:31 saturn kernel: [17199919.844000] EXT3-fs warning (device sdb5):
ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
Nov  5 02:23:31 saturn kernel: [17199919.844000] EXT3-fs warning (device sdb5):
ext3_clear_journal_err: Marking fs in need of filesystem check.



At the end I got my filesystem corrupted! ](*,)

---

### Post by stevenwagner on 2006-11-17
Maybe this thread can help.
[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17224.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17224.html)


Same problem here too...happened during the mkfs.

Nov 17 08:55:55 ss-laptop -- MARK --
Nov 17 09:03:28 ss-laptop kernel: [17600341.780000] usb 4-5: reset high speed USB device using ehci_hcd and address 15
Nov 17 09:03:29 ss-laptop kernel: [17600352.136000] usb 4-5: reset high speed USB device using ehci_hcd and address 15
Nov 17 09:03:29 ss-laptop kernel: [17600368.380000] usb 4-5: reset high speed USB device using ehci_hcd and address 15
Nov 17 09:03:30 ss-laptop kernel: [17600368.628000] usb 4-5: reset high speed USB device using ehci_hcd and address 15
Nov 17 09:03:30 ss-laptop kernel: [17600378.872000] usb 4-5: reset high speed USB device using ehci_hcd and address 15
Nov 17 09:03:30 ss-laptop kernel: [17600379.004000] sd 8:0:0:0: scsi: Device offlined - not ready after error recovery
Nov 17 09:03:30 ss-laptop kernel: [17600379.004000] sd 8:0:0:0: SCSI error: return code = 0x50000
Nov 17 09:03:30 ss-laptop kernel: [17600379.004000] end_request: I/O error, dev sda, sector 796151
Nov 17 09:03:30 ss-laptop kernel: [17600379.004000] printk: 151851 messages suppressed.
Nov 17 09:03:30 ss-laptop kernel: [17600379.004000] lost page write due to I/O error on sda1
Nov 17 09:03:30 ss-laptop last message repeated 9 times
Nov 17 09:03:30 ss-laptop kernel: [17600379.020000] sd 8:0:0:0: SCSI error: return code = 0x10000
Nov 17 09:03:30 ss-laptop kernel: [17600379.020000] end_request: I/O error, dev sda, sector 796391
Nov 17 09:03:33 ss-laptop kernel: [17600389.004000] printk: 924567 messages suppressed.
Nov 17 09:03:33 ss-laptop kernel: [17600389.004000] lost page write due to I/O error on sda1
Nov 17 09:03:38 ss-laptop kernel: [17600394.008000] printk: 870903 messages suppressed.
Nov 17 09:03:38 ss-laptop kernel: [17600394.008000] lost page write due to I/O error on sda1
Nov 17 09:03:43 ss-laptop kernel: [17600399.004000] printk: 869775 messages suppressed.
Nov 17 09:03:43 ss-laptop kernel: [17600399.004000] lost page write due to I/O error on sda1
Nov 17 09:03:48 ss-laptop kernel: [17600404.004000] printk: 870759 messages suppressed.
Nov 17 09:03:48 ss-laptop kernel: [17600404.004000] lost page write due to I/O error on sda1
Nov 17 09:03:53 ss-laptop kernel: [17600409.004000] printk: 864740 messages suppressed.
Nov 17 09:03:54 ss-laptop kernel: [17600409.004000] lost page write due to I/O error on sda1
Nov 17 09:03:58 ss-laptop kernel: [17600414.004000] printk: 865939 messages suppressed.
Nov 17 09:03:58 ss-laptop kernel: [17600414.004000] lost page write due to I/O error on sda1
Nov 17 09:04:03 ss-laptop kernel: [17600419.008000] printk: 861670 messages suppressed.
Nov 17 09:04:04 ss-laptop kernel: [17600419.008000] lost page write due to I/O error on sda1

---

### Post by BatteryCell on 2006-12-13
Same problem
Bump

---

### Post by robertzwo on 2008-02-13
in this similar thread maybe here is the solution
[http://ubuntuforums.org/showthread.php?t=452246](http://ubuntuforums.org/showthread.php?t=452246)

---

