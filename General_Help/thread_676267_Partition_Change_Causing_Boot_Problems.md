---
title: "Partition Change Causing Boot Problems"
date: 2008-01-23
forum: General Help
---

### Post by kevinfitch83 on 2008-01-23
Ok, I made the mistake of re-formatting a drive which Ubuntu mounts during boot. Now Ubuntu freezes during boot and won't start up correctly. I tried formatting the drive back to it's original fs and when that didn't work I tried pulling the drive's mount info out of /etc/fstab. Neither worked. Is their anything else I can try. I'd hate to have to resort to reinstalling. I just got everything set up the way I like.

---

### Post by kevinfitch83 on 2008-01-23
Ok, nevermind. Taking the entry out of Fstab did work. When I made the change I got the original fstab confused with the backup I made.

---

### Post by t20racerman on 2008-01-23
Replace it with what?  Have you got the original still? If so, put that back.

However, there is a bigger issue here - probably a corrupted partition table. I fixed an ubuntu install with partition/boot problems last week.. and heck of a job it was too. If your partition table is corrupted, you need to somehow repair it. 
I used 'testdisc' which is a program you can get on several repair type Cds. you boot up your PC with this and it repairs partitions. Worked a treat for me!

---

