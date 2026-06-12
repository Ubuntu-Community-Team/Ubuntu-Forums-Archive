---
title: "Some contents unreadable"
date: 2007-02-19
forum: General Help
---

### Post by vdhagen on 2007-02-19
Apparently there are different sources of information about my raid5-device /dev/md0:

[LIST]
[*]mdadm reports (after adding 4th disk and 10 hours "reshaping") an array size of 750GB with 4 active/working disks of 250GB.
[*]"properties" (of the mounted device) reports "some contents unreadable" and free space  of 50GB which was correct before adding the 4th disk. Incidentally in the network as well the raid-device appears with the "old" size: 450GB occupied, 50GB free
[/LIST]

Any suggestion how this problem can be resolved?

Oskar

P.S. File transfers so far were no problem in the network.
I am using kernel 2.6.20

---

### Post by vdhagen on 2007-02-19
Apparently growing the array is only part of the job. Extending  the filesystem is also required. In my case
fsck.ext3 /dev/md0
e2fsck -f /dev/md0
resize2fs /dev/md0
finished the job.
Oskar

---

