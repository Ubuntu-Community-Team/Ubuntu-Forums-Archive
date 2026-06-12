---
title: "Problem with update"
date: 2024-05-08
forum: General Help
---

### Post by asai on 2024-05-08
I am trying to run a update/upgrade, but the system tells me that theres no free space.

```

You don't have enough free space in /var/cache/apt/archives/.

```

Running df -H shows this:

```

Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              403M  2.8M  400M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  106G  102G     0 100% /
tmpfs                              2.1G     0  2.1G   0% /dev/shm
tmpfs                              5.3M     0  5.3M   0% /run/lock
/dev/sda2                          2.1G  265M  1.7G  14% /boot
/dev/sda1                          1.2G  6.4M  1.2G   1% /boot/efi
tmpfs                              403M  4.1k  403M   1% /run/user/0

```

Theres lots of space on the 2 disks, so whats is my problem?

---

### Post by ActionParsnip on 2024-05-08
Run:
```

sudo apt clean
sudo apt --purge autoremove

```
You may also want to remove old kernels if you have multiple. I also suggest you clean data from $HOME as your /home folder in part of the root file system rather than it's own.

You need to do some housekeeping

---

### Post by asai on 2024-05-08
> **ActionParsnip said:**
> Run:
```

sudo apt clean
sudo apt --purge autoremove

```
You may also want to remove old kernels if you have multiple. I also suggest you clean data from $HOME as your /home folder in part of the root file system rather than it's own.

You need to do some housekeeping

I have already tried the cleaning, but same issue.
However, I did not check the home folder. Wow... Lots of data!
I did some testing of a backup script. Forgot to turn it of.
There was several months of backup data, not overwriting, but new folders multiple times.

Case resolved :)

---

### Post by ActionParsnip on 2024-05-08
Awesome!

---

