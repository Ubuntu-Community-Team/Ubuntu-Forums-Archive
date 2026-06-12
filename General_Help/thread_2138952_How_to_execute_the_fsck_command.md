---
title: "How to execute the fsck command?"
date: 2013-04-25
forum: General Help
---

### Post by Sly14Cat on 2013-04-25
Alrighty, I want to do a check up on Ubuntu. It's ext4 and the file system is mounted at /dev/sda4. I was goind to do the whole touch /forcefsck but it's a dual boot windows and ubuntu. What command do I use?

---

### Post by dabl on 2013-04-25
You don't fsck the running system -- the partition has to be unmounted.  Easiest method, IMHO, is to make a Parted Magic or GParted Live USB stick or CD, boot that, use the Partition Manager GUI to browse to the hdd and partition that you want, right-click the graphic and choose "check".

As far as the command line utility, take a look at ```
man e2fsck
```

---

### Post by oldfred on 2013-04-25
As dabl says it has to be unmounted.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by oldos2er on 2013-04-25
> **Sly14Cat said:**
> Alrighty, I want to do a check up on Ubuntu. It's ext4 and the file system is mounted at /dev/sda4. I was goind to do the whole touch /forcefsck but it's a dual boot windows and ubuntu. What command do I use?

You can use ```
sudo touch /forcefsck
``` which will cause fsck to be run at next boot up. It won't touch Windows.

---

### Post by Sly14Cat on 2013-04-25
Forgot to mention I used a live cd. Thanks guys

---

