---
title: "Hard disk read-ahead &amp; hdparm"
date: 2007-09-08
forum: General Help
---

### Post by youknow on 2007-09-08
Developing a buffer manager for a database system, I want to find out how many pages the operating system fetches from the disk on every read operation (so that, on every read() I read into the bufferpool as many pages as possible). My questions are the following:

a) Does the value of /sys/block/sda/queue/read_ahead_kb  (typically 128k) decide the amount of data that every read() fetches from the disk ? (this value can also be decided by hdparm -a /dev/sda, but is measured in sectors). If this is true, then I guess that each time I do a read() operation for 128 consecutive kbytes, I can be sure that at most one IO request will reach the disk.

b) hdparm specifies that parameter -m specifies the sector count for the Multiple Sector mode (aka IDE Block mode), which "permits the transfer of multiple sectors per I/O interrupt, rather than the usual one sector  per  interrupt". Are these multiple sectors consecutive (physically) or not? Because I can't see any benefit if they are not consecutive. And if they are indeed consecutive, isn't it the same thing with read_ahead_kb ?

c) Playing around a little with hdparm, I benchmarked my disk (Seagate ST340014A) using the --direct mode (which performs operations with O_DIRECT). Using read_ahead_kb = 128 i got the following (each measurement was repeated 3 times):

$ sudo hdparm -t /dev/sda
/dev/sda:
Timing buffered disk reads:  160 MB in  3.03 seconds =  52.76 MB/sec

Then i used --direct and got:
$ sudo hdparm -t --direct /dev/sda
/dev/sda:
Timing O_DIRECT disk reads:  168 MB in  3.02 seconds =  55.69 MB/sec

I disabled the read_ahead feature (hdparm -A0 /dev/sda). Then I repeated the above and got:
$ sudo hdparm -t /dev/sda
/dev/sda:
Timing buffered disk reads:   30 MB in  3.03 seconds =   9.91 MB/sec

and:
$ sudo hdparm -t --direct /dev/sda
/dev/sda:
Timing O_DIRECT disk reads:   88 MB in  3.04 seconds =  28.98 MB/sec

How do you explain this difference?

Any help would be greatly appreciated...

---

