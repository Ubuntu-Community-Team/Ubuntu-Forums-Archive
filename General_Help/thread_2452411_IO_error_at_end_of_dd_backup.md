---
title: "I/O error at end of dd backup"
date: 2020-10-21
forum: General Help
---

### Post by David_Partridge on 2020-10-21
```
sudo dd bs=16M if=/dev/disk/by-id/ata-KINGSTON_SVP100S296G_312Y10B7Y5SK | pv | dd ibs=16M obs=64K of=/dev/st0l
5723+1 records in29.9MiB/s] [                     <=>                                                                      ]
5723+1 records out
96029466624 bytes (96 GB, 89 GiB) copied, 2912.15 s, 33.0 MB/s
89.4GiB 0:48:32 [31.4MiB/s] [                       <=>                                                                    ]
dd: error writing '/dev/st0l': Invalid argument
dd: closing output file '/dev/st0l': Input/output error
set +v

```

Any idea what I've done wrong that causes the IO error?

Thanks
David

---

### Post by TheFu on 2020-10-21
A full tape?

If corruption could be causing the issue, try using ddrescue.  ddrescue is dd, but it won't stop due to read or write failures. I've never tried it with a tape drive either.

---

### Post by David_Partridge on 2020-10-21
No definitely not a full tape - its a small disk drive and an LTO-4 tape

---

### Post by dinkidonk on 2020-10-21
Since you do not specify how much data (count= argument) to copy, there will be an I/O error when EOF is reached and this may be what troubles you. Try to specify the amount of data to copy and see what happens.

---

### Post by HermanAB on 2020-10-22
Simplify:
sudo cat /dev/disk/by-id/ata-KINGSTON_SVP100S296G_312Y10B7Y5SK > /dev/st0l

---

