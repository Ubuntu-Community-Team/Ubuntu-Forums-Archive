---
title: "Problem with mount point when mounting a squashfs backup"
date: 2021-03-30
forum: General Help
---

### Post by cscj01 on 2021-03-30
I created a squashfs backup of my filesystem with the command```
sudo mksquashfs / /media/butch/SysBack/sys-backup.sqsh -e media home dev run mnt proc sys tmp
```

Then I tried to mount it with the following commands```
sudo mkdir /mnt/sys-backup
sudo mount /media/butch/SysBack/sys-backup.sqsh /mnt/sys_backup -t squashfs -o loop
```When I issue the mount command, I get the following message> mount: /mnt/sys_backup: mount point does not exist.Clearly the mount point does exist.  Here are the commands to reach it```
butch@cp1:~$ cd /mnt/sys-backup
butch@cp1:/mnt/sys-backup$ ls
```Why is the system telling me the mount point does not exist?

---

### Post by yetimon_64 on 2021-03-30
> **cscj01 said:**
> ...```
sudo mkdir /mnt/sys-backup
sudo mount /media/butch/SysBack/sys-backup.sqsh /mnt/sys_backup -t squashfs -o loop
```...

You created /mnt/sys-backup but are trying to mount to /mnt/sys_backup. Try changing the underscore in the mount location to a "-" (dash) instead of an "_" (underscore).

> Why is the system telling me the mount point does not exist?  The underscore in the mount command is a "typo" you created the mount folder with a dash symbol not an underscore.

---

### Post by cscj01 on 2021-03-30
Thank you for discovering my obvious mistake.  I must have looked at the statement for 30 minutes or more without noticing.

---

