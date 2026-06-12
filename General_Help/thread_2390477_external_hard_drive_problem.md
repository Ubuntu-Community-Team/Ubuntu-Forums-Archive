---
title: "external hard drive problem"
date: 2018-04-29
forum: General Help
---

### Post by Lloydb39 on 2018-04-29
I have an external hard drive. When I turn it on it usually appears on the Unity taskbar (16.04). Now it doesn't. The disk utility says it is OK with one bad sector. How do I get the rascal back so I can back up some files?

---

### Post by Autodave on 2018-04-29
If the bad sector is the boot sector, you are probably not going to get anything. Couple of things you can try: another machine, another cable, try chilling the drive: put it in your fridge for an hour and then try it.

Chilling it rarely works, but once in a great while it does. It at least is worth a try at this point.

---

### Post by yancek on 2018-04-29
If it shows a bad sector, you could try running the fsck command on whichever drive and whichever partition it is.

---

### Post by vanadium on 2018-04-29
Some diagnosis may help first, but it involves opening the terminal.
- Plug in the terminal, wait a few seconds then issue the command
```

dmesg | tail -n 40
[code]
This shows the 40 or so last terminal messages, which indicate what the kernel "sees" when you attach the drive, and how it tries to deal with it.
[code]
sudo blkid  | grep -v loop
mount | grep dev/

```
Shows the partitions seen by the system and these that were effectively mounted.
If mounted, then identify your external drive's partition and try to mount it: error message may give a hint on what is going on.

Only after debugging would I freeze it, nail it or do other things with it.

---

### Post by dragonfly41 on 2018-04-29
OP might watch this video .. it gives some interesting background on drive bad sectors..

[https://www.grc.com/sr/whatitdoes.htm](https://www.grc.com/sr/whatitdoes.htm)

Personally I have not used SpinRite but it sounds interesting.   It is not free.

---

### Post by Lloydb39 on 2018-05-01
> **vanadium said:**
> Some diagnosis may help first, but it involves opening the terminal.
- Plug in the terminal, wait a few seconds then issue the command
```

dmesg | tail -n 40
[code]
This shows the 40 or so last terminal messages, which indicate what the kernel "sees" when you attach the drive, and how it tries to deal with it.
[code]
sudo blkid  | grep -v loop
mount | grep dev/

```
Shows the partitions seen by the system and these that were effectively mounted.
If mounted, then identify your external drive's partition and try to mount it: error message may give a hint on what is going on.

Only after debugging would I freeze it, nail it or do other things with it.

I got this:
lloyd@linux:~$ dmesg | tail -n 40
[395031.618393] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618404] ata4.00: cmd 61/08:a8:47:0a:c1/00:00:32:00:00/40 tag 21 ncq 4096 out
                         res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[395031.618409] ata4.00: status: { DRDY }
[395031.618414] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618424] ata4.00: cmd 61/08:b0:6f:0a:c1/00:00:32:00:00/40 tag 22 ncq 4096 out
                         res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[395031.618429] ata4.00: status: { DRDY }
[395031.618434] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618444] ata4.00: cmd 61/08:c0:27:04:c1/00:00:32:00:00/40 tag 24 ncq 4096 out
                         res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[395031.618449] ata4.00: status: { DRDY }
[395031.618454] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618464] ata4.00: cmd 61/08:c8:87:04:c1/00:00:32:00:00/40 tag 25 ncq 4096 out
                         res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[395031.618469] ata4.00: status: { DRDY }
[395031.618474] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618484] ata4.00: cmd 61/08:d0:9f:04:c1/00:00:32:00:00/40 tag 26 ncq 4096 out
                         res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[395031.618489] ata4.00: status: { DRDY }
[395031.618494] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618504] ata4.00: cmd 61/08:d8:cf:04:c1/00:00:32:00:00/40 tag 27 ncq 4096 out
                         res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[395031.618509] ata4.00: status: { DRDY }
[395031.618514] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618524] ata4.00: cmd 61/08:e0:f7:04:c1/00:00:32:00:00/40 tag 28 ncq 4096 out
                         res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[395031.618530] ata4.00: status: { DRDY }
[395031.618534] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618544] ata4.00: cmd 61/08:e8:7f:05:c1/00:00:32:00:00/40 tag 29 ncq 4096 out
                         res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[395031.618550] ata4.00: status: { DRDY }
[395031.618554] ata4.00: failed command: WRITE FPDMA QUEUED
[395031.618564] ata4.00: cmd 61/10:f0:9f:05:c1/00:00:32:00:00/40 tag 30 ncq 8192 out
                         res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[395031.618570] ata4.00: status: { DRDY }
[395031.618576] ata4: hard resetting link
[395032.949848] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[395033.102085] ata4.00: configured for UDMA/133
[395033.102137] ata4: EH complete

---

### Post by dragonfly41 on 2018-05-01
This old thread had similar errors and pointed to failing PSU ...

[https://ubuntuforums.org/showthread.php?t=2272486](https://ubuntuforums.org/showthread.php?t=2272486)

---

### Post by Lloydb39 on 2018-05-01
I ran fdisk -l and got this, which sounds ominous:

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *            63 1936860659 1936860597 923.6G 83 Linux
/dev/sda2       1936860660 1953520064   16659405     8G  5 Extended
/dev/sda5       1936860723 1953520064   16659342     8G 82 Linux swap / Solaris


Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.

---

### Post by Lloydb39 on 2018-05-01
That's interesting. I have the same motherboard, different power supply. I'll try to check it out.

---

### Post by Lloydb39 on 2018-05-02
If anyone is still following, I finally figured out the device name and ran fsck on it. It came back with "this doesn't bode well, but we can try to fix it" and I hit OK. It ran literally thousands of fixes on "inodes" and blocks and I had to OK each one. Finally I quit before it was finished. It did show the disk in the Unity bar but it wouldn't mount. After that the fsck command did not have any effect on it. At this point I guess it is toast (It's probably a 10 year old drive I pulled out of an old computer) but before I toss it, is there anything I can do to make sure?

---

### Post by dragonfly41 on 2018-05-02
Much depends on what monetary value you attach to any data still in your drive.

The old but proven SpinRite discussed in post #7 above comes with a price of $89.
But I have never had reason to use it, I'm only referring to user cases I have read.
The developer's GRC web site is respected.

If you don't think that is a worthwhile investment you can try testdisk which is free.

There are other "last chance saloon" strategies you might try.
Here is one discussion about swapping logic boards.  But requiring identical drives.
[https://www.zdnet.com/article/a-word-of-warning-on-hard-disk-recovery-by-swapping-logic-boards/](https://www.zdnet.com/article/a-word-of-warning-on-hard-disk-recovery-by-swapping-logic-boards/)

And there is the old trick (see post #2) of wrapping faulty drive in polythene wrapping (to keep it dry) and placing in freezer.
But again I've managed to recover my drives without taking such steps. The warning I have read is that the freezer approach probably only gives you one chance to dump any files before it gives up the ghost so you have to be ready with an empty drive to save any recovered data.

---

### Post by Lloydb39 on 2018-05-02
Progress. Using a thread I found, I managed to reformat and mount the old drive and even create a home folder on it. But it won't let me put anything in it because I don't have permissions. I tried chown command but it didn't work. Anybody?

---

### Post by dragonfly41 on 2018-05-02
"Reformat" means that the internal data had zero value. Why try to get a failing drive work rather than extracting data? I'm puzzled.

---

### Post by Lloydb39 on 2018-05-02
Don't know exactly how but I think I have it fixed. With the help above and some other stuff I found, I managed to format the external drive and change ownership and permissions on it. Now it mounts again and I can copy files to it. Thanks to all. I'll mark it solved.

---

### Post by Lloydb39 on 2018-05-04
Dragonfly. It was just a backup disk. I wiped what was on it with the format, then replaced it with the same date from my main hard drive. The original problem was that it didn't mount. Fixed now.

---

