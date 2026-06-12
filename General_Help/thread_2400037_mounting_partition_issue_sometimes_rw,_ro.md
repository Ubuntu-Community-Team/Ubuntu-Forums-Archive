---
title: "mounting partition issue: sometimes rw, ro"
date: 2018-09-01
forum: General Help
---

### Post by herbert tamayo on 2018-09-01
Hi, I am working with Kubuntu 18.0.4 LTS, I am having an issue with my Windows 10 partition, this one is mounted automatically by Kubuntu, yet the problem is sometime it is mounted in rw mode and sometimes in ro. This is the entire parameter when it's mounted on rw mode:

```

fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0

```

When it is mounted on ro mode, this is the paramater:
```

fuseblk ro,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0

```

To mount this partition I use Dolphin and then one click on the icon related to this partition (device)

I use /etc/mtab to obtain the mounted mode for the device described above. I've already checked /etc/fstab but I couldn't find any entry for this partition.

My question is: what is the way to avoid the ro mounted mode for this partition and instead always get rw mode?

All the best

Herbert

---

### Post by Impavidus on 2018-09-02
There's no entry for this partition in /etc/fstab unless you created one yourself. You need one if you want this partition to mount automatically at boot.

Normally when you mount the partition using your file manager (I don't use Dolphin, but most should be similar), it will be mounted rw. However, if Windows hasn't cleanly unmounted the filesystem, Linux cannot mount it rw, but may mount it ro instead. So the solution is to make sure Windows always cleanly unmounts the partition when it shuts down. Have you disabled FastStartup in Windows? Windows can switch it back on automatically at updates.

---

