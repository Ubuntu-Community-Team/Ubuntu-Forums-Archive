---
title: "sg utilities are getting hung on SSDs"
date: 2017-02-28
forum: General Help
---

### Post by viswesh2 on 2017-02-28
We are running 4.4.0-31-generic in our systems and we have started seeing the below behavior of late.

We run utilities like hdparm and sg_inq utilities on all  of our devices and what we see of late is that, these commands get hung for days and never complete for one random device (commands on other devices of the same make works fine at the same time)

These processes are getting stuck in ,

```
ps -fe | grep hdparm
root       792 38087  0 18:39 ?        00:00:00 hdparm -I /dev/sdh1
root      6717  6116  0 19:24 pts/4    00:00:00 sudo hdparm -I /dev/sdh1
root      6718  6717  0 19:24 pts/4    00:00:00 hdparm -I /dev/sdh1
```

```
~$ sudo cat /proc/6718/stack 
[<ffffffff81589436>] scsi_block_when_processing_errors+0x86/0x100
[<ffffffff815865b4>] scsi_ioctl_block_when_processing_errors+0x44/0x50
[<ffffffff81598e31>] sd_ioctl+0x61/0x110
[<ffffffff813b49d1>] blkdev_ioctl+0x251/0x8c0
[<ffffffff81236cc1>] block_ioctl+0x41/0x50
[<ffffffff8121063d>] do_vfs_ioctl+0x2dd/0x4c0
[<ffffffff81210899>] SyS_ioctl+0x79/0x90
[<ffffffff817f6f36>] entry_SYSCALL_64_fastpath+0x16/0x75
[<ffffffffffffffff>] 0xffffffffffffffff
```


When i did a sysrq dump of all threads, i could see the error handling thread waiting to be woken up. Seems to be a deadlock. Has anyone seen something similar.

In the next occurrence, what all other information should i collect to debug this further.

I have enabled scsi logging for errors now.

---

### Post by DuckHook on 2017-02-28
...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

