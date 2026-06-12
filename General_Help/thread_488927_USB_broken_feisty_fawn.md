---
title: "USB broken feisty fawn"
date: 2007-06-30
forum: General Help
---

### Post by yagerd001 on 2007-06-30
I'm running two Feisty Fawn boxes, one as a server, one as my desktop.  My server box recognizes & mounts my 1gb flash drive, but the desktop doesn't, gives me this with dmesg:

[67681.014000] sdb : READ CAPACITY failed.
[67681.014000] sdb : status=0, message=00, host=1, driver=00 
[67681.014000] sdb : sense not available. 
[67681.014000] sdb: Write Protect is off
[67681.014000] sdb: Mode Sense: 00 00 00 00
[67681.014000] sdb: assuming drive cache: write through

The flash drive comes on for maybe half a second when I physically insert the flash drive, then goes out.

Is their a daemon that should be running?  Any clues?

---

