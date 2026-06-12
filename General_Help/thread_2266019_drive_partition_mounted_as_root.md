---
title: "drive partition mounted as root"
date: 2015-02-19
forum: General Help
---

### Post by mohan-kiran on 2015-02-19
I have two laptop running Ubuntu 14.10. Both of these have a directory /media/Data
```
drwxr-xr-x 2 root root 4096 Feb 19 16:36 /media/Data/    #before mounting
```

The following entry exits in /etc/fstab of both the laptops
```
UUID=XXXXXXXXXXXXXXXXXXXXXX /media/Data ext4 defaults 0 0
```
However, after boot up, one of the laptop mounts the drive as root user and in the other it mounts as the logged-in user(with sudo powers)
```
drwxr-xr-x 3 root root 4096 Feb 18 00:32 /media/Data/       # laptop 1
drwxr-xr-x 3 user user 4096 Feb 18 00:32 /media/Data/       # laptop 2
```

1. Why the difference?
2. How can I get the drive mounted as logged in user?

---

### Post by Morbius1 on 2015-02-19
[1] The permissions of the mount point before a partition is mounted has no affect on the permissions of the mounted partition.

[2] On this laptop:
> drwxr-xr-x 3 root root 4096 Feb 18 00:32 /media/Data/       # laptop 1
Change ownership to user:user:
```
sudo chown user:user /media/Data
```
But remember to only do this after the partition has been mounted.

[3] Why are they different:

My guess is that somewhere along the line you already did the chown command on laptop2. If you were to rip out that drive on laptop2 and send it to me it would still be owned by user:user since ownership and permissions are embedded within the partition itself.

---

### Post by mohan-kiran on 2015-02-19
Thanks Morbius1.
You are right.

---

