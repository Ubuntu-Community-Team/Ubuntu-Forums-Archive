---
title: "Massive ZFS Crash During Copy on Lubuntu 16.04"
date: 2016-07-11
forum: General Help
---

### Post by jaw3000 on 2016-07-11
I am experiencing severe and reproducible crashes when copying files to a ZFS-formatted disk using Lubuntu 16.04 as well as a wiped ZFS pool. The exact problem is listed in detail below. For background, I am copying off of an external read-only HFS+ formatted disk to the internal ZFS pool. I have for over six years been using ZFS-Fuse on a different pool and an old 2010 version of Ubuntu on the same system, and have never had a problem or an error during copies. I have decided it was finally time to upgrade the OS to a newer version, now that ZFS is kernel integrated, and I get met with errors. This specific ZFS pool is located on a new internal HD, and has been destroyed and recreated multiple times since this error began. Again, copying off the same HFS+ external HD to an internal ZFS pool has never caused errors before. ZFS has always worked flawlessly for me - until this OS upgrade.

At this point, I don’t know if the problem is inherent to Lubuntu/PCManFM, or ZFS-on-Linux, or the kernel, or the new HD (SMART checks show no errors), or installing Lubuntu under a LVM arrangement, or something else. Maybe someone can help me out.

Exact Scenerio:
I begin to copy a folder of files onto the ZFS pool using the PCManFM file manager GUI. Soon after the copy begins, it seems to halt. This happens 4-5 times. The odd 5th time, the copy goes without issue.

Eventually (though not at first), the system comes to a halt. The whole system seems to become read-only. Attempting to save a doc tells me the drive is “read-only.” It isn’t. Firefox and Chrome stop loading pages (assumingly because they can’t write to disk). If I check the system logs, I see an endless appendage (posted below).

When I try to shut down, I get one of two things. One is the Lubuntu GUI shutdown just won’t work. Nothing happens. The other is the system goes to a black screen, where the same endlessly scrolling log appears - and the system never shuts down. I have to manually power it off.

Upon restart, the same thing happens every time. I get dropped into BusyBox with just a prompt and no messages. Typing “exit” will not commence a system boot. If I manually power off and restart a second time, I get the Ubuntu startup menu. Selecting Ubuntu, I get dropped back into BusyBox, but this time I get the following messages

“Lvmetad is not active yet, using direct activation during sysinit
/dev/mapper/lubuntu--vg-root contains a files system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.

/dev/mapper/lubuntu--vg-root; UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
Fsck exited with status code 4
The root filesystem on /dev/mapper/lubuntu--vg-root requires a manual fsck”

I can manually run a fsck /dev/mapper/lubuntu--vg-root, agree yes to all, and then exit and Lubuntu will boot normally. Upon reboot, everything works like nothing happened. Until I go to copy a file again, and 4-5 times the same error process will occur. This has happened to me at least seven times now, and is usually reproducible with the exact same result.

The first time this happened, the ZFS pool “Storage2” was actually completely wiped following the reboot. Before shutdown, a “zpool status” showed two errors on the files which was being copied when the error occurred. After the reboot, ZFS showed no storage pools at all. A “zpool import Storage2” returned no storage pools. Gedit reported the drive as unformatted (while it had reported it as ZFS). The pool was completely wiped. After recreating the pool, and subsequent error sequences and reboots, the pool has never wiped and has always remounted without issue. In fact, before the reboot “zpool status” reports the error on the file being copied, yet after a reboot, no errors are even reported. A “zpool scrub” reports no errors.

Any assistance would be greatly appreciated! If this should be reported as a bug or would be better off asked elsewhere, please direct me to the proper channel. 

System Log (Random segment):

```
Jul 11 21:25:13 Ubuntu zed: eid=7241 class=io pool=Storage2
Jul 11 21:25:13 Ubuntu kernel: [ 4856.668073] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 11 21:25:13 Ubuntu kernel: [ 4856.668080] ata2.00: failed command: WRITE DMA
Jul 11 21:25:13 Ubuntu kernel: [ 4856.668087] ata2.00: cmd ca/00:00:e8:56:10/00:00:00:00:00/e9 tag 0 dma 131072 out
Jul 11 21:25:13 Ubuntu kernel: [ 4856.668087]          res 50/00:00:1f:6e:c0/00:00:d1:01:00/e1 Emask 0x40 (internal error)
Jul 11 21:25:13 Ubuntu kernel: [ 4856.668090] ata2.00: status: { DRDY }
Jul 11 21:25:13 Ubuntu zed: eid=7242 class=data pool=Storage2
Jul 11 21:25:13 Ubuntu zed: eid=7243 class=io pool=Storage2
Jul 11 21:25:13 Ubuntu zed: eid=7244 class=data pool=Storage2
Jul 11 21:25:13 Ubuntu kernel: [ 4856.756323] ata2.00: configured for UDMA/133
Jul 11 21:25:13 Ubuntu kernel: [ 4856.756371] ata2: EH complete
Jul 11 21:25:13 Ubuntu kernel: [ 4856.756716] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.2
Jul 11 21:25:13 Ubuntu kernel: [ 4856.764057] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 11 21:25:13 Ubuntu kernel: [ 4856.764065] ata2.00: failed command: WRITE DMA
Jul 11 21:25:13 Ubuntu kernel: [ 4856.764076] ata2.00: cmd ca/00:00:e8:57:10/00:00:00:00:00/e9 tag 0 dma 131072 out
Jul 11 21:25:13 Ubuntu kernel: [ 4856.764076]          res 50/00:00:af:be:c0/00:00:d1:01:00/e1 Emask 0x40 (internal error)
Jul 11 21:25:13 Ubuntu kernel: [ 4856.764082] ata2.00: status: { DRDY }
Jul 11 21:25:13 Ubuntu kernel: [ 4856.788328] ata2.00: configured for UDMA/133
Jul 11 21:25:13 Ubuntu kernel: [ 4856.788376] ata2: EH complete
Jul 11 21:25:13 Ubuntu kernel: [ 4856.878504] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.2
Jul 11 21:25:13 Ubuntu zed: eid=7245 class=io pool=Storage2
Jul 11 21:25:13 Ubuntu kernel: [ 4856.884065] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0


```

---

### Post by wildmanne39 on 2016-07-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by jaw3000 on 2016-07-12
After spending more time troubleshooting, it appears the issue might be related to faulty Broadcom wifi drivers. I'm not entirely sure uninstalling them have helped yet, but wanted to point it out in case anyone else experiences similar problems. Marking this as solved.

---

