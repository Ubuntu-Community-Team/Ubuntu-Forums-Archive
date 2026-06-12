---
title: "Why is Ext4 read-only mount faster?"
date: 2020-05-09
forum: General Help
---

### Post by dinkidonk on 2020-05-09
I have a 1TB HDD which is attached to a RbPi and used as NAS for backups, downloads, DLNA and so on. Files are constantly being written to and deleted from the drive, thus I expect the filesystem to be pretty messy when the drive is near filled. I usually leave at least 50GiB of space free at all time. When the drive is full, I copy the contents of the drive to an encrypted (LUKS) storage drive, erase it and start over again. When I do this copy procedure, the drive is mounted through an USB3->SATA adapter and when the drive is mounted as read-write, the average transfer speed is about 30MiB/sec which takes about 8 hours to complete and the drive is "grinding" quite heavily. When i mount the drive as read-only, the average transfer speed is more than doubled, about 65MiB/sec which causes the copy procedure to take less than 4 hours and there is no grinding at all. All indexing is disabled, and I suspect this behaviour to be caused by the Ext4 file system driver which tries to optimize content (or free space) on the drive for better performance - but I'm not sure.

 So, what could cause this odd behaviour?

Thanks!

---

### Post by lvm on 2020-05-09
Have you tried mounting it as rw but with noatime option?

---

### Post by dinkidonk on 2020-05-11
> **lvm said:**
> Have you tried mounting it as rw but with noatime option?

Nope, I have not thought of that :-k

I will definitely try to mount both source and destination with **noatime** and see how that inflicts the transfer speeds ASAP. Thanks a lot for the suggestion! :-D

---

