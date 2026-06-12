---
title: "NTFS partition won't mount on startup"
date: 2007-07-23
forum: General Help
---

### Post by Anacondo on 2007-07-23
Hi.

I have a barebone PC with Ubuntu Server 7.04 installed. It has a NTFS partition which I share with other computers in my network via Samba. I'm using ntfs-3g so others can modify it. I would like this partition to be automatically mounted on startup, but I've had no luck so far.

After system startup the partition seems to be mounted, but I can see no data. Windows shows an error when trying to access the remote location. Here is the output from mount:

```
/dev/disk/by-uuid/06CFE8A6742D91FA on /mnt/oldmusic type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
```

I always have to unmount and remount the partition by hand after a system startup. Then it starts working as it should. I even tried adding an entry in /etc/rc.local for unmounting & remounting the partition in every startup, but for some reason it didn't work.

Here is my fstab entry:

```
# /dev/sda2
UUID=06CFE8A6742D91FA /mnt/oldmusic   ntfs-3g   silent,umask=0,nls=utf8     0       0
```

Hope you can help. Thanks in advance.

---

### Post by nol1ght on 2007-07-23
in fstab try to put this line (works for me)
```
/dev/sda2     /media/oldmusic ntfs-3g  defaults,locale=en_US.utf8   0    0
```

---

### Post by Anacondo on 2007-07-23
> **nol1ght said:**
> in fstab try to put this line (works for me)
```
/dev/sda2     /media/oldmusic ntfs-3g  defaults,locale=en_US.utf8   0    0
```

Thanks, I already tried that. Doesn't work.

---

