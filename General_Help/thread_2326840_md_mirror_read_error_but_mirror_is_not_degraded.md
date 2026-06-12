---
title: "md mirror: read error but mirror is not degraded"
date: 2016-06-05
forum: General Help
---

### Post by trtrmitya on 2016-06-05
Hello,

I am using Ubuntu 15.10.
I have md raid1 with 2 components: sda2+sdb2.  I replaced (how swap) sda disk, new disk was detected as sdc, and I started mirror resync.
During resync I have the following in dmesg:

```
[Sun Jun  5 15:44:00 2016] sd 1:0:0:0: [sdb] tag#27 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[Sun Jun  5 15:44:00 2016] sd 1:0:0:0: [sdb] tag#27 Sense Key : Medium Error [current] [descriptor] 
[Sun Jun  5 15:44:00 2016] sd 1:0:0:0: [sdb] tag#27 Add. Sense: Unrecovered read error - auto reallocate failed
[Sun Jun  5 15:44:00 2016] sd 1:0:0:0: [sdb] tag#27 CDB: Read(10) 28 00 33 05 f9 a0 00 00 08 00
[Sun Jun  5 15:44:00 2016] blk_update_request: I/O error, dev sdb, sector 856029601
[Sun Jun  5 15:44:00 2016] ata2: EH complete
[Sun Jun  5 15:44:00 2016] md/raid1:md126: sdb: unrecoverable I/O read error for block 754205056

```
So I treat is so that during recovery there was a read error from disk sdb.

But mirror resync was not stopped and finished successfully.  Mirror is healthy according to /proc/mdstat.

How is it possible?  Is my mirror in consistent state?

Thanks.

---

### Post by wildmanne39 on 2016-06-05
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
> I/O error, dev sdb, sector 856029601usually means your hard drive is failing.

---

### Post by trtrmitya on 2016-06-06
The question was how the mirror could be synchronized from disk which has unrecoverable read errors.


Also, consider the following excerpt from monthly mirror check:

```
[FONT=Menlo]Jun  5 00:57:01 watson2-17 mdadm[1088]: RebuildStarted event detected on md device /dev/md126[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.306137] ata5.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.306169] ata5.00: irq_stat 0x40000008[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.306184] ata5.00: failed command: READ FPDMA QUEUED[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.306204] ata5.00: cmd 60/80:08:00:17:01/00:00:00:00:00/40 tag 1 ncq 65536 in[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.306204]          res 41/40:00:1f:17:01/00:00:00:00:00/40 Emask 0x409 (media error) <F>[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.306251] ata5.00: status: { DRDY ERR }[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.306265] ata5.00: error: { UNC }[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.308428] ata5.00: configured for UDMA/133[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.308441] sd 4:0:0:0: [sde] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.308444] sd 4:0:0:0: [sde] tag#1 Sense Key : Medium Error [current] [descriptor] [/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.308446] sd 4:0:0:0: [sde] tag#1 Add. Sense: Unrecovered read error - auto reallocate failed[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.308449] sd 4:0:0:0: [sde] tag#1 CDB: Read(16) 88 00 00 00 00 00 00 01 17 00 00 00 00 80 00 00[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.308451] blk_update_request: I/O error, dev sde, sector 71455[/FONT]
[FONT=Menlo]Jun  5 00:57:03 watson2-17 kernel: [1243223.308504] ata5: EH complete[/FONT]
[FONT=Menlo]Jun  5 00:59:23 watson2-17 kernel: [1243363.835505] md: md126: data-check done.[/FONT]



```

So during md raid1 check there was a read error from one of it's components.  Shouldn't this component become failed as a result?

---

