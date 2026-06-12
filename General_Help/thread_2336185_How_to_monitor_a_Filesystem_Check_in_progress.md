---
title: "How to monitor a Filesystem Check in progress?"
date: 2016-09-05
forum: General Help
---

### Post by bcschmerker on 2016-09-05
I am currently looking over the problem of monitoring filesystem checks in progress on an Ubuntu® 16.04.1-LTS desktop rig (Advanced MIcro Devices® Athlon64® X2 5600+, RS780G/SB710 chipset) with a history of hit-and-miss unmounts in both ext4 and BTrFS during shutdown.  The involved partitions are on three Toshiba® MQ01ABD050 hard disc drives holding the partitions for /usr, /opt, and /srv in ext3 on /dev/sdb; /var in BTrFS on /dev/sdc; and /home in BTrFS on /dev/sdd.  The Console confirms start of fsck.ext4 and fsck.btr during startup, but the built-in ATi® RS780 northbridge GPU switches over to X for login before the fsck's complete.  My rig has an unused EIA 574 port, /dev/ttyS0, available for a remote terminal.  How does one go about this task?

---

