---
title: "Shrinking and growing RAID1 partitions"
date: 2017-03-26
forum: General Help
---

### Post by jvacek on 2017-03-26
Hello people, so I'm running a dedicated server and it has 2x 3TB HDDs. The initial setup from the provider created 4 md partitions in RAID1, and the two I need to tinker with are md2 (1TB, mounted to /) and md3 (1.7TB, mounted to /home).

I really do not need 1TB for the / partition, and have tried to shrink it down to 30GB with [this guide]("https://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid"). However, this shrank only the virtual partition of md2, and did not make any changes on sda3 and sdb3, which are both still 1TB. When I then tried to extend the md3 size to take up all the space I took away from md2, it wouldn't take the newly freed up space into account, as that is still part of the other partition.

[Here's the current state of my disks and mdadm.]("http://pastebin.com/raw/bjTaVH5Z")

Can anyone please guide me through shrinking the sda3 and sdb3 and then taking this freed up space up with sda4 and sdb4 so that I can extend my md3? Essentially, in the end, md2, sda3 and sdb3 (/ mount) should be 30GB while md3, sda4 and sdb4 (/home mount) should be around 2.6TB.


Thanks a lot in advance!

---

