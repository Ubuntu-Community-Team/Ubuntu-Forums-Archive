---
title: "how to manage premission for user group for internal harddisk partitions"
date: 2013-07-04
forum: General Help
---

### Post by manidhwn on 2013-07-04
someone suggest me that for managing permission for accessing the partitions of hard disk you should add users to group and  now i have found from askubuntu.com that how to add user to groups.
  But i not get the way how to add permissions for users in such a way  that they not have access to specific hard disk partition but they have  access to other partition without use of admin password?
  after mounting partition in admin user when i go to properties and  then to permission and their try to change the premissions something  like access to files/folder and groups then when i change the groups and  going to save it automatically changed to previous setting before i can  save?
  i am using ubuntu 12.04 LTS
  so please tell how to manage the permission for user for access to hard disk partitions?
      :confused:

---

### Post by Impavidus on 2013-07-04
Suppose you have partitions X, Y and Z. Use fstab to automatically mount the partitions at, let's say, /media/X, /media/Y and /media/Z. Set the permissions for these mount points so that the group has full access but others don't. Make groups X, Y and Z and set the group of /media/X to X, /media/Y to Y and /media/Z to Z. Put every user with access to partition A in group A etc. and it should work.

---

### Post by efflandt on 2013-07-04
What file system is on the partitions? If it is FAT related or NTFS, they have no concept of *nix file permissions, so you can only set blanket directory or file ownership or permissions for the entire partition using mount options (or in /etc/fstab). You cannot change individual directory or file permissions on that.

But see "The bind mounts." in "man mount". That may allow you to bind and remount subdirectories or files on those types of file systems with different owner/permissions.

Otherwise use some type of Linux type file system, unless you also need to access the files from Windows, etc.

---

### Post by manidhwn on 2013-07-04
what is etc/fstab ?
is these are softwares which needed to install from sofware center?

---

### Post by Impavidus on 2013-07-04
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I don't think you have to install anything, just make some modifications to your file system and configuration. To be more specific we'll need more information.

---

### Post by Morbius1 on 2013-07-04
If you want these folks to help you providing the output of the following commands would be helpful so they can see what you're taking about:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by manidhwn on 2013-07-05
thanks to all for reply 
i got the solutions by installing sofwares

i have tried mountmanager and storage device manager for mangaing the partition.

Both sofware are good but storage device manager is easy while mount manager have more functionalities.

\\:D/\\:D/\\:D/\\:D/

---

