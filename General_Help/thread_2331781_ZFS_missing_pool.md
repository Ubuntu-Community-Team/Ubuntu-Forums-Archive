---
title: "ZFS missing pool"
date: 2016-07-25
forum: General Help
---

### Post by wmccull on 2016-07-25
Hi all...
Hopefully there is some Guru type 'GOD' figure that knows how to help me as i am .. S.T.U.M.P.E.D ! and frantically running around as all the pictures of my daughter are on there with no other backups.

i had a disk failure on my ZFS pool called 'storage' and followed a few guides online about clearing the I/O failures to determine if they were real or not.

Im now stuck with a so called corrupt drive ' sdd' missing from my pool and unable to replace the disk with the larger drive 'sdf' as the pool doesn't exists.

 commands ive tried..

zpool import storage
cannot import 'storage': one or more devices is currently unavailable

.............................................................

root@mediahome:~# zpool status
no pools available
root@mediahome:~# zpool status -x
no pools available
......................................................................................

zpool import -d /dev
   pool: storage
     id: 9268253743039060642
  state: UNAVAIL
 status: One or more devices are missing from the system.
 action: The pool cannot be imported. Attach the missing
        devices and try again.
   see: [http://zfsonlinux.org/msg/ZFS-8000-6X](http://zfsonlinux.org/msg/ZFS-8000-6X)
 config:

        storage      UNAVAIL  missing device
          raidz1-0   ONLINE
            sdb1     ONLINE
            sdc1     ONLINE
          sde        ONLINE

        Additional devices are known to be part of this pool, though their
        exact configuration cannot be determined.

......................................
root@mediahome:~# zpool replace storage sdd sdf
cannot open 'storage': no such pool



Id really appreciate some help and guidance on this.

Thanks in advance folks

Wmccull

---

### Post by wmccull on 2016-08-24
This post is still active on the chance anyone can help ?

---

### Post by Geoffrey_Arndt on 2016-08-25
There are _so few_ Ubuntu users with ZFS that your best bet might be to look at other distros and perhaps even the BSD unix folks to get an answer.   OpenIndiana is also based on Solaris, might check them out as well.

Here's an article re "Antergos" . . apparently first distro to offer ZFS install option during the OS installer process:

[http://linuxbsdos.com/2016/02/22/antergos-the-first-linux-distribution-with-zfs-support-during-installation/](http://linuxbsdos.com/2016/02/22/antergos-the-first-linux-distribution-with-zfs-support-during-installation/)

[https://antergos.com/](https://antergos.com/)

---

