---
title: "K3B/cdrecord takes forever to close burn"
date: 2013-11-09
forum: General Help
---

### Post by bizshop on 2013-11-09
OK, not forever, but 221 seconds. Only 144 seconds to write the data, 221 to fixate/close the disk. It complains about being unable to flush cache. Any ideas on how to fix or where this cache is?

Here is k3b log:

[cdrecord] Writing  time:  144.225s
[cdrecord] Average write speed  12.3x.
[cdrecord] Min drive buffer fill was 100%
[cdrecord] Fixating...
[cdrecord] Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
[cdrecord] CDB:  35 00 00 00 00 00 00 00 00 00
[cdrecord] status: 0x2 (CHECK CONDITION)
[cdrecord] Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
[cdrecord] Sense Key: 0x0 No Additional Sense, Segment 11
[cdrecord] Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
[cdrecord] Sense flags: Blk 0 (not valid)
[cdrecord] cmd finished after 201.635s timeout 200s
[cdrecord] Trouble flushing the cache
[cdrecord] Fixating time:  221.935s
[cdrecord] /usr/bin/wodim: fifo had 4079 puts and 4079 gets.
[cdrecord] /usr/bin/wodim: fifo was 0 times empty and 3865 times full, min fill was 93%.
[cdrecord] BURN-Free was never needed.

---

### Post by tgalati4 on 2013-11-09
During that wait, open a terminal:

```
dmesg | tail -40
```

See what is happening inside the system.  

I don't know enough about what happens during the disk fixation, but something is not responding so *k3b* just waits.  Try the same burning with *brasero* or *cdw* and see if you get the same wait.

---

