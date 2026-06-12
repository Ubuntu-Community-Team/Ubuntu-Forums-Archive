---
title: "Lost WRITE support of NTFS drives"
date: 2014-10-28
forum: General Help
---

### Post by onesojourner on 2014-10-28
I was having some issues with an exfat sd card so I messed around installing some packages in the saftware center and now I have lost the ability to write to any of my ntfs drives. Here is my fstab file currently. I tried to modify the 1storage entry, but running sudo mount -a I get /1storage seems to be mounted read-only. Then I restarted but I am still unable to write to my drives. Here is my fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=5d37f4db-4354-4c64-be62-8c6b0d69e44f /               ext4    errors=remount-ro 0       1
# /1storage was on /dev/sdf3 during installation
UUID=5C8C87558C87291A /1storage       ntfs    defaults,umask=000,gid=46 0       0
# /1storageP5 was on /dev/sdg2 during installation
UUID=B8E47E70E47E312C /1storageP5     ntfs    defaults,umask=007,gid=46 0       0
# /2storage was on /dev/sdd2 during installation
UUID=CC3E79883E796BF8 /2storage       ntfs    defaults,umask=007,gid=46 0       0
# /3storage was on /dev/sdc1 during installation
UUID=4384CF507B4BA7FC /3storage       ntfs    defaults,umask=007,gid=46 0       0
# /4storage was on /dev/sdb1 during installation
UUID=1093A72B764BF60D /4storage       ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdd1 during installation
UUID=e88548f0-cc73-45b3-81ea-51d9c8530e61 none            swap    sw              0       0
# swap was on /dev/sdf5 during installation
UUID=bc16d38e-b46b-41d9-a1cb-1c5dc334e644 none            swap    sw              0       0
# swap was on /dev/sdg5 during installation
UUID=668f84a7-0141-490c-a980-3bf79f1bff57 none            swap    sw              0       0
```

---

### Post by ajgreeny on 2014-10-28
I think either of the two following line patterns should work for you, changing to your required mountpoints and UUIDs, of course.
```
UUID=66E53AEC54455DB2 /mountpoint    ntfs-3g        auto,user,rw 0 0
UUID=66E53AEC54455DB2 /mountpoint  ntfs    defaults    0    0
```
I believe the second of the lines is the more recent version to do this, but both should still work though it will depend on the permissions you want for which users.

Do you need to restrict use to members of group with gid 46 or do you want all users to have access?

---

### Post by onesojourner on 2014-10-28
> **ajgreeny said:**
> I think either of the two following line patterns should work for you, changing to your required mountpoints and UUIDs, of course.
```
UUID=66E53AEC54455DB2 /mountpoint    ntfs-3g        auto,user,rw 0 0
UUID=66E53AEC54455DB2 /mountpoint  ntfs    defaults    0    0
```
I believe the second of the lines is the more recent version to do this, but both should still work though it will depend on the permissions you want for which users.

Do you need to restrict use to members of group with gid 46 or do you want all users to have access?


Alright, modified your second line and gave that a try. That gave root access but know one else.  I would like everyone to have read write access to the drives. Thanks.

---

### Post by ajgreeny on 2014-10-29
What about the first of my two lines?

Alternatively, I think you could run ```
sudo chmod 666 /mountpoint
``` on the mountpoint of the partition to give it read/write permissions to all.

I do not use ntfs as I have no Windows in the house now, so I'm not totally sure about this, but it's worth a try.

---

### Post by yancek on 2014-10-29
Linus permissions don't apply to windows partitions.  You need to use fmask, dmask and/or umask settings.  The link below provides a pretty detailed explanation.

[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by ajgreeny on 2014-10-29
> **yancek said:**
> Linus permissions don't apply to windows partitions.  You need to use fmask, dmask and/or umask settings.  The link below provides a pretty detailed explanation.

[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
I did wonder about that but it is such a long time since I needed to use an ntfs partition that I honestly could not remember.

The first of the two line patterns I showed above should have given read/write permission if I read your linked thread correctly.

---

### Post by yancek on 2014-10-29
The umask options the OP shows should give world rwx permissions to 1storage and rw permissions for user and group and nothing for others.  I don't use windows partitions and only came across this when trying to help someone figure out how to create a partition where only one user and root could have any access (rwx) and users/others no access at all.  If it was working before, I think there is some other problem.

---

