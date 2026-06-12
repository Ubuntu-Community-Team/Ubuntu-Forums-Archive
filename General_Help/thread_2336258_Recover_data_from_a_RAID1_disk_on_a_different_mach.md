---
title: "Recover data from a RAID1 disk on a different machine"
date: 2016-09-06
forum: General Help
---

### Post by Mad_Pink on 2016-09-06
I was running an Ubuntu server and it crashed over the weekend, that's a seperate issue.

Right now, I just need to try and get data off of one of the hard drives for a project that is due very soon.

I took out the drive and put it into another machine and then booted up a Live CD.

I cannot mount the drive, it tells me "unknown file system "linux_raid_member"  (using  mount /dev/sda3 /mnt/back)

What can I do to get the drive mounted so that I can copy data off of it?

---

### Post by SeijiSensei on 2016-09-06
Try using "sudo mount -t ext4 /dev/sda3 /mntpoint".  I've found that works if the disk was part of a RAID1 array.

However usually a RAID1 will continue working with the faulty disc in the array.  Did that not happen for you?

---

### Post by Mad_Pink on 2016-09-06
> **SeijiSensei said:**
> Try using "sudo mount -t ext4 /dev/sda3 /mntpoint".  I've found that works if the disk was part of a RAID1 array.
I tried that, I get: "wrong fs type, bad option, bad superblock on /dev/sda3, missing codepage or helper program, or other error"

I also tried ext3 and got the same result.

> However usually a RAID1 will continue working with the faulty disc in the array.  Did that not happen for you?

Not sure what you mean, if you are referring to the server, I am still diagnosing what went wrong. Unfortunately, I am not even getting a BIOS screen when it boots, so I am not sure what's happening there.

---

### Post by Mad_Pink on 2016-09-06
After reading some other similar posts the following steps worked for me.

I installed mdadm and ran this command:

mdadm --assemble --scan

this mounted all of the partitions and let me get all my files, and more importantly should preserve my job!

Thanks!

---

