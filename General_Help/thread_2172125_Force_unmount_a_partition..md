---
title: "Force unmount a partition."
date: 2013-09-03
forum: General Help
---

### Post by chakri78 on 2013-09-03
I have two hosts configured with drbd. I want to make sure no one is using the partition before i do a switchover. Is there a command to forcefully unmount a partition? i tried fuser -ku but not killing all the processes using the partition.

Thanks,

---

### Post by maestrobwh1 on 2013-09-03
sudo umount -l /dev/sdxy

that is a lower case L

I think it stands for lazy unmount...

---

