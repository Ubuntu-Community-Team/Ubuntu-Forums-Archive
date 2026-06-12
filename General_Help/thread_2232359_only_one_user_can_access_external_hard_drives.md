---
title: "only one user can access external hard drives"
date: 2014-07-01
forum: General Help
---

### Post by Cat_Geek on 2014-07-01
Hi,

I share my computer with another user and we each use seperate user accounts. We have an external hard drive and I'd like to set up my computer so that we can both access it simoltaneously.

I think this problem started after I upgraded to xubuntu 14.04. In the past, devices used to mount to /media/[DEVICE] and could be accessed by any user, but I've noticed that now they mount to /media/[USER]/[DEVICE] and can only be accessed by USER.

The problem is that when external drives are plugged in, only the current user is able to access them. If the other user wants to access the device, the first user has to unmount it from within that account, before the device can be mounted from the second account.

Any suggestions?

Thanks!

EDITED TO ADD:

actually, I don't remember well how it used to work, or if I ever got it to work the way I want. I've done several installs recently with very different configurations, so my memory might be confused. Either way, I'd like to be able to set up my computer so that we can both access the external hard drive at the same time.

---

### Post by yancek on 2014-07-01
I would suggest creating a directory as a mount point in the /mnt directory for each partition on the external drive, then putting an entry in the filesystem table (/etc/fstab file).  Some detailed information and examples of entries are at the Ubuntu site below.  If you have problems post back with info on the names and number of partitions.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

