---
title: "Ryzen 3 2200G Graphics not working on Ubuntu 18.04"
date: 2018-09-28
forum: General Help
---

### Post by bizhat on 2018-09-28
I was using PC with Intel i7 950 running Ubuntu 18.04

I replaced it with new PC with Ryzen 3 2200 G.

On new PC, graphics did not work. I had to use new kernel (ubuntu mainline) to get display to work properly.

```

boby@ok-pc-01:~$ uname -r
4.18.10-041810-generic
boby@ok-pc-01:~$ 

```

Now my zfs volumes wont work. When i run zpool ls, i get

```

root@ok-pc-01:~# zpool ls
The ZFS modules are not loaded.
Try running '/sbin/modprobe zfs' as root to load them.
root@ok-pc-01:~# 

```

When i run modprobe zfs, i get error

```

root@ok-pc-01:~# modprobe zfs
modprobe: FATAL: Module zfs not found in directory /lib/modules/4.18.10-041810-generic
root@ok-pc-01:~# 

```

Any idea how i get my zfs disks back ?

Look like this new mainline kernal have no support for zfs. Anyway i can get this new AMD graphics work on default Ubuntu kernel ?

---

