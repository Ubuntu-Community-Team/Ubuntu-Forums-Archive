---
title: "ext4 external HDD, wrong permissions on school computer"
date: 2013-04-23
forum: General Help
---

### Post by jonashendrickx on 2013-04-23
the students have a user 'student' while the it administration has the user icti

when i connect my external hdd to the school computer it detects my NTFS and EXT4 partitions. I can read the NTFS partition and write like it should, but my EXT4 partition is owned by the icti IT administrator account

On my laptop I can read and write to the ext4 partition like it should after chown'ing it to my user account. 

Is there a way to fix this so I can read the ext4 partition at school? I have a meeting with the IT Support tomorrow, they will take a look at it.

I can see ext4_portable mounted in /media/ext4_portable just like ntfs_portable. But ext4_portable simply won't open :(

---

### Post by dino99 on 2013-04-23
[http://ubuntugenius.wordpress.com/2012/06/07/ubuntu-hardware-permissions-how-to-set-ownership-of-drive-or-partition-internal-external-hard-disks/](http://ubuntugenius.wordpress.com/2012/06/07/ubuntu-hardware-permissions-how-to-set-ownership-of-drive-or-partition-internal-external-hard-disks/)

using : sudo chmod 644 /media/your_partition
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

