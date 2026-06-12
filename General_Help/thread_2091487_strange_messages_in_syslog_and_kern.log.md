---
title: "strange messages in syslog and kern.log"
date: 2012-12-05
forum: General Help
---

### Post by rnerwein on 2012-12-05
hello
the messages i show you i receive since a long time. but now i decide to open thread because it hassle me. the messages are:
1.  Dec  5 12:36:18 tschang kernel: [ 3478.248878] sd 10:0:0:0: [sdd] Test WP failed, assume Write Enabled
Dec  5 12:36:18 tschang kernel: [ 3478.250873] sd 10:0:0:0: [sdd] Asking for cache data failed
==> be sure - there is no "sdd" on the system. even the "sdd" is changing to "sdg", "sdf"
        but never to a disk which is physikal attached ???!! (i tried gparted, fdisk parted ...)
        any idea ?

2. Dec  5 12:36:14 tschang kernel: [ 3471.707847] [drm] nouveau 0000:03:00.0: Register 0x00004030 not found in PLL limits table
==> is this may be regarded with VLC (music) ? i can't really prove it but this message is driving me crazy - got hundreds of thausend of them.
any idea ?

the culprit is my own kernel monitor - but about 5500 system calls per second ( if started with an interval of one second) and about 12000 lines of code - i am to lazy to search for the guildy syscall. must come with kernel vmlinuz-3.2.0-33
;-)

---

