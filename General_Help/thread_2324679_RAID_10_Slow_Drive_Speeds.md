---
title: "RAID 10 Slow Drive Speeds"
date: 2016-05-15
forum: General Help
---

### Post by sronk510 on 2016-05-15
I have a Media/Web server setup with Ubuntu Server 14.04.04LTS. It is setup with LVM and uses KVM to run two virtual machines also Ubuntu Server. I have four 2 TB HDDs setup in RAID 10. Typically when I run hdparm I get 270MBs read speeds but randomly that number will drop to 5-20MBs. As I said it is completely random and at one point went nearly 2 weeks without happening. According to MegaCli there have been no smart status flags tripped so I haven't checked drive health yet. Iv'e tried shutting down the VM's, KVM, NFS and really any service that the host is using and the slow speeds still persist. I'm beginning to think that either a drive(s) or RAID card is at fault. I figured I would ask to see if anyone else has had a similar issue. 

From here my next step will be to take each drive and test it individually for health. And if they all check out then perhaps a fcsk is in order.

Thank in advance...

---

