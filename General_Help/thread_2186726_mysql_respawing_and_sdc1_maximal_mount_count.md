---
title: "mysql respawing and sdc1 maximal mount count"
date: 2013-11-08
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-11-08
I have no clue as to what this is all about:

mark@Lexington:~$ dmesg | tail

[   68.706421] init: mysql main process (2283) terminated with status 1
[   68.706450] init: mysql main process ended, respawning
[   69.033429] init: mysql post-start process (2284) terminated with status 1
[   69.040734] type=1400 audit(1383930049.185:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=2330 comm="apparmor_parser"
[   70.715600] init: mysql main process (2334) terminated with status 1
[   70.715629] init: mysql respawning too fast, stopped
[  118.850001] kjournald starting.  Commit interval 5 seconds
[  118.850015] EXT3-fs (sdc1): warning: maximal mount count reached, running e2fsck is recommended
[  118.857196] EXT3-fs (sdc1): using internal journal
[  118.857203] EXT3-fs (sdc1): mounted filesystem with ordered data mode

(sdc1) is a 1gig usb thumb drive. It is plugged into a usb port all the time, but I very rarely read or write to it. Not more than once a month, at most.

I didn't install a mysql to my knowledge.

Are these problems serious? Can they be reasonably ignored?

---

