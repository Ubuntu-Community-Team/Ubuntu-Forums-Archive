---
title: "[SOLVED] Mount subdirectory in fstab using mount --bind"
date: 2007-11-16
forum: General Help
---

### Post by baruthegreat on 2007-11-16
Hello all,

I have been mounting a subdirectory on a RAID array to a mount point closer to /, so that the path name is shorter.

```
$ sudo mount --bind /mnt/md0/directory /directory
```

Is there a way to put this in /etc/fstab for automounting on reboot? I've tried

```
/mnt/md0/directory   /directory   reiserfs        defaults        0       0
```

but when I try

```
$ sudo mount -a
```

I get

```
mount: /mnt/md0/bart_backups is not a block device
```

Thanks.

---

### Post by Bolorino on 2007-11-18
Try in fstab

```
/mnt/md0/directory   /directory none    bind  0  0
```

---

### Post by baruthegreat on 2007-11-19
Thanks, Bolorino. That works.

Where would one find out about using "none" for the filesystem type? Or using bind in the options? I haven't found anything mentioning "none" in the fstab man page, or in the man page for mount.

Can one use any option valid for mount in fstab?

---

### Post by Bolorino on 2007-11-21
Baruthegreat, happy to know it worked :-)

I found a similar problem with an nfs filesystem mounted with "bind".

Not sure, but I think the point is that the "bind" option is used to remount something that you already have mounted elsewhere.

---

