---
title: "mt-st and stinit timeouts appear to be ignored"
date: 2016-12-23
forum: General Help
---

### Post by David_Partridge on 2016-12-23
After issuing an mt-st -f /dev/st0 erase I keep getting 

```
INFO: task mt-st:11282 blocked for more than 120 seconds.
```

and associated tracebacks in syslog even though I have short timout set to 180 and long timeout set to 14400

/etc/stinit.def:
```
# HP Ultrium 460
#
manufacturer="HP" model = "Ultrium 2-SCSI" {
scsi2logical=1
can-bsr=1
auto-lock=1
two-fms=0
drive-buffering=1
buffer-writes
read-ahead=1
async-writes=1
can-partitions=0
fast-mteom=0
sysv=1
#
# If your stinit supports the timeouts:
timeout=180 # 3 minutes
long-timeout=14400 # 4 hours
#
mode1 blocksize=0 compression=0 # 200 GB, LTO2 _NO_ compression
mode2 blocksize=0 compression=1 # 400 GB, LTO2 compresses
mode3 disabled=1
mode4 disabled=1


```

---

### Post by David_Partridge on 2016-12-23
Hmmm it's worse than I thought - most of the time I cannot use the alias device names.

---

### Post by David_Partridge on 2016-12-23
Hmmmm Running stinit manually fixes the problem

Dave

---

