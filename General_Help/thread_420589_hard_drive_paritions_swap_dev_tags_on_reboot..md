---
title: "hard drive paritions swap /dev tags on reboot."
date: 2007-04-23
forum: General Help
---

### Post by pirothezero on 2007-04-23
I installed feisty yesterday. Today I go to reboot and I get a file system check failed because it couldn't find the 3 uuid'ed paritions in the fstab file because of the following:

When I do fdisk -l it has my os drive that has three partitions, /, /home, and swap as /dev/sdc1 through sdc3 and a storage drive of 300 gigs as /dev/sda1. 

When I installed it yesturday I had my os drive 36 gig raptor as /dev/sda1 through sda3. 

No cables have been touched and this has happened before a few days ago wasn't expecting it after a clean install though. 

Has anyone every heard of this?

---

