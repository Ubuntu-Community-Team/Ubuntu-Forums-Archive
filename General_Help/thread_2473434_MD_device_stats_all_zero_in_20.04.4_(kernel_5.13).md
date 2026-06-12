---
title: "MD device stats all zero in 20.04.4 (kernel 5.13)"
date: 2022-04-04
forum: General Help
---

### Post by nano-bashford on 2022-04-04
Hi

I work with a number of machines that are running Ubuntu 20.04, all with several Software RAID devices. On those running the 5.11 kernel, as expected, there are valid stats for the /dev/md* devices in /sys/block/md*/stat files. However, for machines that have upgraded to the newer 5.13 kernel, the /sys/block/md*/stat files contain all zeros.

For one machine that had upgraded to 20.04.4 and kernel 5.13, have reverted just the kernel packages to 5.11 and can the stats are now correctly populated again.

Is this a known problem? If so, is a fix/workaround available? If not, I'm happy to provide further information that may help.

Exact kernel versions tested are:
5.13.0-37-generic -- stats all zero
5.11.0-46-generic -- stats populated as expected

---

