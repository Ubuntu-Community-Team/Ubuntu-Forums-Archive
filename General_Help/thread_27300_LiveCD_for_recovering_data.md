---
title: "LiveCD for recovering data"
date: 2005-04-15
forum: General Help
---

### Post by patrickallo on 2005-04-15
I've got to recover some data from my dad's windows-machine which refuses to boot (as usual no backup available so I have to save his files before repairing XP). Is there any way to run LiveCD (Ubuntu or DSL) and access data on his HD? (Do I have to mount the disc in some or other way?)

Anyone advice?


Note: I told him this was the right time to switch to a real OS, but I haven't convinced him yet.

---

### Post by accuser on 2005-04-15
Any Live CD should do you, although I think that there are specifically some boot disks (1.44M) and cds that provide specific tools for data recovery. Have a look at some of the specialist Knoppix cds.

To mount C: drive read-only at /mnt/c (assuming it is the first partition on the first ide drive):

```
$ mkdir -p /mnt/c ; mount -o ro /dev/hda1 /mnt/c
```

---

