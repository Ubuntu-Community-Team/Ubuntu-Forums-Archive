---
title: "Partitioning problem  - &quot;read only filesystem&quot;"
date: 2007-03-11
forum: General Help
---

### Post by epimer on 2007-03-11
Since getting a laptop, I've decided to change my desktop box over to a server. So, with that in mind, I installed Edgy server on the 80 GB hard drive (previous home of my XP installation), backed up my data, and set about formatting the 250 GB drive (previous home of my Edgy desktop installation) for use as a data partition.

I used cfdisk to create a blank partition (cfdisk /dev/sdb), mkfs to create an ext3 filesystem on it (mkfs -t ext3 /dev/sdb) and added it to my fstab (mounted on /mnt/sdb, options default,users, 0 in the last two columns). However, I don't have write access to the drive - trying to cp or mv anything across from the command line returns an error suggesting it is a "read-only" filesystem.

Does anyone know what I've done wrong?

Thanks.

---

### Post by taurus on 2007-03-11
If it's ext3, you just need to change the ownership of the mount point from root to your username.  So, where do you mount it and what is your login name?

---

### Post by epimer on 2007-03-11
> **taurus said:**
> If it's ext3, you just need to change the ownership of the mount point from root to your username.  So, where do you mount it and what is your login name?

I mounted it to /mnt/sdb, and my login name is (surprise) epimer. How do I change the ownership?

---

### Post by taurus on 2007-03-11
```
sudo chown -R surprise:surprise /mnt/sdb
ls -la /mnt/sdb
```

---

### Post by epimer on 2007-03-11
> **taurus said:**
> ```
sudo chown -R surprise:surprise /mnt/sdb
ls -la /mnt/sdb
```

That did the trick. Thanks a lot!

---

