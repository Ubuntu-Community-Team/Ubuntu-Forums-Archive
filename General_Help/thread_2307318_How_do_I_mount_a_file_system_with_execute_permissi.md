---
title: "How do I mount a file system with execute permissions on ubuntu?"
date: 2015-12-23
forum: General Help
---

### Post by Emanuel_Frank on 2015-12-23
[COLOR=#111111][FONT=Ubuntu]I want to do this so that I can install games on separate hard drives on steam but I can't because I keep getting an error saying New Steam library folder must be on a filesystem mounted with execute permissions. I am using FAT32.[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2015-12-24
Hi and welcome.

You can't use FAT32 for that.

---

### Post by HermanAB on 2015-12-24
Yup.  You have to use a real UNIX file system.  Any one of ext3, ext4, btrfs, xfs or jfs will work.

---

### Post by Emanuel_Frank on 2015-12-24
I formatted it to ext4 but then when I create a file on steam, it says this drive is read only and it won't let me create the steam folder and when I try to change the permissions for the drive, it says i'm not the owner.

---

### Post by Dennis N on 2015-12-24
> **Emanuel_Frank said:**
> I formatted it to ext4 but then when I create a file on steam, it says this drive is read only and it won't let me create the steam folder and when I try to change the permissions for the drive, it says i'm not the owner.

You can change ownership of a file system on a drive by changing ownership of the mount point. Then you will have the permissions you need:

If the mount point was /mnt/data, then

```
sudo chown -R user:user /mnt/data
```

Put your user name in both places of user:user

---

### Post by Emanuel_Frank on 2015-12-24
How do I know what my mount point is?

---

### Post by yancek on 2015-12-24
Partitions on external drives are generally available under the /media/username directory.

---

