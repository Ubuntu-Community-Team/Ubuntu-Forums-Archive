---
title: "IDE probe bug - increase log buffer size without recompiling?"
date: 2007-01-24
forum: General Help
---

### Post by IntuitiveNipple on 2007-01-24
During initrd boot, then again during kernel start-up, probing of 4 IDE drives on a Promise FastTrak TX2000 FakeRAID IDE controller causes massive repeated errors.
The system is booting from hda, uses hdb for data, hdc & hdd are DVDs, hde,hdf,hdg & hdh are the drives on the TX2000.

At both problem-points the drives are being repeatedly seek-ed beyond their final sectors for long periods (10-30 seconds each time), causing some terrible head-banging noises and sometimes rendering the drives inoperable until a power-off, pause, and cold-boot.

I know *why* its happening, but need some more info to track down the source code file where the bug is.

The problem is the drives contain a Mirror+Stripe (RAID 1+0) array, with hde+hdf being mirror.1 on IDE2, and hdg+hdh being mirror.2 on IDE3.

When the standard IDE probe reads the partition table from the first drive (the table representing the RAID0 array hde+hdf), some of the LBA sector addresses are actually on the 2nd drive, but because the dmraid drivers aren't loaded at this point the standard kernel IDE probing logic tries to seek past the end of the physical disk containing the partition table.
If it compared the sector-address of the seek with the size of the disk, it could avoid this issue.

I am trying to find a way to increase the kernel log buffer size so I can capture the messages just before the problem begins, in order to locate the bug in the IDE probe logic and fix it. I'm trying to avoid having to recompile the kernel to do this.

As it is, the amount of error reports ( thousands generated at each error stage) push the prior messages out of the buffer so when the system has finally started there's nothing but the errors in the log files.

Here's just a small section from /var/log/messages (its the same in dmesg & kern.log). I've included the start and end blocks of one period of errors - notice especially the time-stamp of the messages - the error cycle lasts almost a minute.

---BEGIN---
```
Jan 20 21:31:18 butch syslogd 1.4.1#18ubuntu6: restart.
Jan 20 21:31:18 butch kernel: [17179633.896000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179633.928000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179633.928000] hdg: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179633.928000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179633.936000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179633.936000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179633.936000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179633.976000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179633.976000] hdg: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179633.976000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179634.004000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179634.004000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179634.004000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179634.020000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179634.020000] hdg: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179634.020000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179634.020000] PDC202XX: Secondary channel reset.
Jan 20 21:31:19 butch kernel: [17179634.048000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179634.048000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179634.048000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179634.048000] PDC202XX: Primary channel reset.
Jan 20 21:31:19 butch kernel: [17179634.068000] ide3: reset: success
Jan 20 21:31:19 butch kernel: [17179634.096000] ide2: reset: success
Jan 20 21:31:19 butch kernel: [17179634.112000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179634.112000] hdg: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179634.112000] ide: failed opcode was: unknown
Jan 20 21:31:19 butch kernel: [17179634.112000] end_request: I/O error, dev hdg, sector 135203040
Jan 20 21:31:19 butch kernel: [17179634.112000] printk: 18 messages suppressed.
Jan 20 21:31:19 butch kernel: [17179634.160000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:31:19 butch kernel: [17179634.160000] hdg: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:31:19 butch kernel: [17179634.160000] ide: failed opcode was: unknown
```
---END---
```
Jan 20 21:32:08 butch kernel: [17179709.344000] PDC202XX: Primary channel reset.
Jan 20 21:32:08 butch kernel: [17179709.392000] ide2: reset: success
Jan 20 21:32:08 butch kernel: [17179709.452000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:32:08 butch kernel: [17179709.452000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:32:08 butch kernel: [17179709.452000] ide: failed opcode was: unknown
Jan 20 21:32:08 butch kernel: [17179709.488000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:32:08 butch kernel: [17179709.488000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:32:08 butch kernel: [17179709.488000] ide: failed opcode was: unknown
Jan 20 21:32:08 butch kernel: [17179709.544000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:32:08 butch kernel: [17179709.544000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:32:08 butch kernel: [17179709.544000] ide: failed opcode was: unknown
Jan 20 21:32:08 butch kernel: [17179709.576000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:32:08 butch kernel: [17179709.576000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:32:08 butch kernel: [17179709.576000] ide: failed opcode was: unknown
Jan 20 21:32:08 butch kernel: [17179709.576000] PDC202XX: Primary channel reset.
Jan 20 21:32:08 butch kernel: [17179709.624000] ide2: reset: success
Jan 20 21:32:08 butch kernel: [17179709.684000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 20 21:32:08 butch kernel: [17179709.684000] hde: task_in_intr: error=0x04 { DriveStatusError }
Jan 20 21:32:08 butch kernel: [17179709.684000] ide: failed opcode was: unknown
Jan 20 21:32:08 butch kernel: [17179709.684000] end_request: I/O error, dev hde, sector 135203032
Jan 20 21:32:10 butch kernel: [17179711.528000] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 20 21:32:10 butch kernel: [17179711.640000] Netfilter messages via NETLINK v0.30.
```

---

