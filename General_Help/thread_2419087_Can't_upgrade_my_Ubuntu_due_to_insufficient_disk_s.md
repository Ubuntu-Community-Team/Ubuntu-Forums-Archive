---
title: "Can't upgrade my Ubuntu due to insufficient disk space on /boot"
date: 2019-05-16
forum: General Help
---

### Post by fadeout01 on 2019-05-16
Ubuntu 14.04.6 LTS


Hi all! I have an issue with upgrading.
When I run ```
do-release-upgrade
``` it is ending up after  with a message:

```
Calculating the changesNo candidate ver:  libavcodec54
No candidate ver:  libgsl0ldbl
No candidate ver:  linux-image-3.13.0-151-generic
No candidate ver:  linux-image-3.13.0-46-generic
No candidate ver:  linux-image-extra-3.13.0-151-generic
No candidate ver:  linux-image-extra-3.13.0-46-generic

Not enough free disk space

The upgrade has aborted. The upgrade needs a total of 57.7 M free
space on disk '/boot'. Please free at least an additional 6,966 k of
disk space on '/boot'. You can remove old kernels using 'sudo apt
autoremove' and you could also set COMPRESS=xz in
/etc/initramfs-tools/initramfs.conf to reduce the size of your
initramfs.

Restoring original system state


Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
=== Command terminated with exit status 1 (Thu May 16 15:15:57 2019) ===
```

```
dpkg -l | grep linux-image
``` shows this:
```
rc  linux-image-3.13.0-151-generic              3.13.0-151.201                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-170-generic              3.13.0-170.220                                       amd64        Signed kernel image generic
rc  linux-image-3.13.0-46-generic               3.13.0-46.79                                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-151-generic        3.13.0-151.201                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic         3.13.0-46.79                                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                         3.13.0.170.181                                       amd64        Generic Linux kernel image
ii  linux-image-virtual                         3.13.0.170.181                                       amd64        This package will always depend on the latest minimal generic kernel image.

```

```
sudo apt-get autoremove
``` says nothing but:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

```
df -h
```:```
Filesystem                    Size  Used Avail Use% Mounted on
udev                          233M  4.0K  233M   1% /dev
tmpfs                          49M  372K   49M   1% /run
/dev/vda4                      15G  9.3G  4.2G  70% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
none                          5.0M     0  5.0M   0% /run/lock
none                          245M     0  245M   0% /run/shm
none                          100M     0  100M   0% /run/user
/dev/vda2                      92M   39M   49M  45% /boot
https://webdav.yandex.ru:443   11G  6.8G  4.3G  62% /mnt/yd

```


```
uname -r
```:```
3.13.0-170-generic

```

I found this theme [https://ubuntuforums.org/showthread.php?t=2362183](https://ubuntuforums.org/showthread.php?t=2362183) but I'm not sure if it fits my system.
I'm not sure which kernels I can remove without harming the system.

---

### Post by kc1di on 2019-05-16
Your using 3.13.0-170-generic, you can safely remove the others and that should free up some space.  after you remove the kernel you can then run ```
sudo apt autoremove 
``` and it should remove the associated files that are no longer needed.

---

### Post by Impavidus on 2019-05-16
It doesn't look like any other kernels are installed. A 92MB /boot partition is just too small. It may have been fine in the past, but no more. The smallest that works reasonably is about 300MB, but I don't see why anyone would make a /boot partition smaller than 500MB on a modern hard drive. Just to be future-proof.

Furthermore, it's best to upgrade to the next version of Ubuntu before your current version reaches end-of-life. You're a bit late. I suggest you make a larger /boot partition and then a fresh install of 16.04 or 18.04.

---

### Post by fadeout01 on 2019-05-16
> **kc1di said:**
> Your using 3.13.0-170-generic, you can safely remove the others and that should free up some space.  after you remove the kernel you can then run ```
sudo apt autoremove 
``` and it should remove the associated files that are no longer needed.
```
sudo apt autoremove
E: Invalid operation autoremove

```

---

### Post by fadeout01 on 2019-05-16
Ok thanks! I will reinstall it. It seems I have no other way to resolve this situation.

---

### Post by oldrocker99 on 2019-05-16
I have a 64GB SSD which is never more than ~40% full. The whole system can, in fact, run in 32GB.

Reinstallation is exactly how to do it. You should make a separate /home partition during the install; selecting "Something Else" when it shows up, and doing this:[https://www.psychocats.net/ubuntu/installseparatehome](https://www.psychocats.net/ubuntu/installseparatehome)

Also, I've never done anything with /boot; I just leave it alone, and have had no problems in 9 years.

---

### Post by rsteinmetz70112 on 2019-05-16
You may want to look into the /boot partition and see is there is stuff in there you can delete or if it's a separate partition you may want to expand the partition and the filesystem.

---

