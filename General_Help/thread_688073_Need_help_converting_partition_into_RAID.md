---
title: "Need help converting partition into RAID"
date: 2008-02-05
forum: General Help
---

### Post by kinetic87 on 2008-02-05
Hi.  I currently have a server running Ubuntu 7.10 which has a root/boot partition, a swap partition, and a large /home partition on a single hard drive.  Recently, I recieved another hard drive that I would like to add to the /home directory using RAID0.  I don't want to format the original partition since it holds user data.

The way I used to do this was to create an /etc/raidtab file describing the various partitions (in this case sda3 and hdb1), then use mkraid to create the /dev/md0 device, then go through with an ext3 resizing utility to make the filesystem cover both drives.

However, the mkraid utility doesn't seem to exist in any of the Ubuntu packages, and I cannot figure out how to use mdadm to do this without destroying the contents of the first drive.

Thanks,
Kinetic87

---

