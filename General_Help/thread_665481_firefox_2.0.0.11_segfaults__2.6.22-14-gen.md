---
title: "firefox 2.0.0.11 segfaults  2.6.22-14-gen"
date: 2008-01-12
forum: General Help
---

### Post by godfree2 on 2008-01-12
firefox is acting up again
2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
Mozilla Firefox 2.0.0.11, Copyright (c) 1998 - 2007 mozilla.org

I did a complete REMOVE of firefox and it still crashes even in safe-mode

firefox-debug

[INDENT]...
[00000455] main input debug: thread 2729872272 joined (input/input.c:412)
[Thread -1492935792 (LWP 3962) exited]
[00000446] main playlist debug: thread 2802031504 joined (playlist/playlist.c:248)
[00000446] main playlist: stopping playback
[00000446] main playlist debug: deleting playlist item `mms://a695.v8752f.c8752.g.vm.akamaistream.net/7/695/8752/1199910843000/origin.media.cbc.ca/windows/toronto/ondemand/audio/wigt-dakin-recovery.wmv'
[00000444] main private debug: removing all video outputs
[00000444] main private debug: removing all audio outputs
[00000444] main private debug: removing module "memcpy"

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1484543088 (LWP 3947)]
0xb76ea7bd in vfprintf () from /lib/tls/i686/cmov/libc.so.6[/INDENT]

.... safe-mode

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1221269824 (LWP 11443)]
0xb7f9f4e7 in ?? () from /usr/lib/firefox/libmozjs.s


Is there any point in reporting to the firefox devs?

---

