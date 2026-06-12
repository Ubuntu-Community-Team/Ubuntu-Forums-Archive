---
title: "[SOLVED] Added a new HDD... problems?"
date: 2007-10-28
forum: General Help
---

### Post by LauraSakura on 2007-10-28
I've been running Ubuntu on my laptop for a long time, and wanted to try it on my desktop. I installed a second EIDE Hard drive as a slave to my original, and partitioned it and installed Ubuntu 7.10. Ubuntu is on the new hard drive and Win XP is on the master drive. Both operating systems boot and run fine, but my syslogs, kernel logs, etc have been spamming  me with this:

... kernel: [ 1482.039872] sd 1:0:0:1: ioctl_internal_command return code = 8000002
... kernel: [ 1482.039880]    : Sense Key : Medium Error [current] 
... kernel: [ 1482.039884]    : Add. Sense: Unrecovered read error
... kernel: [ 1482.072432] sd 1:0:0:1: [sdc] Unit Not Ready
... kernel: [ 1482.072440] sd 1:0:0:1: [sdc] Sense Key : Medium Error [current] 
... kernel: [ 1482.072445] sd 1:0:0:1: [sdc] Add. Sense: Unrecovered read error
... kernel: [ 1482.123996] sd 1:0:0:1: [sdc] READ CAPACITY failed
... kernel: [ 1482.124004] sd 1:0:0:1: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
... kernel: [ 1482.124009] sd 1:0:0:1: [sdc] Sense Key : Medium Error [current] 
...kernel: [ 1482.124013] sd 1:0:0:1: [sdc] Add. Sense: Unrecovered read error
... kernel: [ 1482.139929] sd 1:0:0:1: [sdc] Test WP failed, assume Write Enabled
... kernel: [ 1482.151791] sd 1:0:0:1: ioctl_internal_command return code = 8000002

The thing is... I'm not even sure what it is that it is complaining about. My computer has 2 internal HDD, 1 External, 2 CD Rom drives, a floppy drive, and built in card reader slot. I figure even though everything seems to be working, it wouldn't complain this much unless there was a real problem. Anyone have any idea what is going on?

---

### Post by LauraSakura on 2007-10-28
Ah... I figured it out but thought I would leave it up here if anyone else has similar problems. Turns out it was a problem with the built in card reader (I had left an empty SD card inside)

---

