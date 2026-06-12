---
title: "Enlarging an existing partition"
date: 2016-07-09
forum: General Help
---

### Post by Nutria on 2016-07-09
Hi,

xubuntu 16.04

I've got a 640GB drive "sdb" wih a 93GiB partition sdb5, and 503GiB of unallocated space.  I'm trying to use gparted to enlarge (currently unmounted) sdb5 into that unallocated space, with zero luck.  I've uploaded screen shots, specifically one showing how the Resize/Move button is greyed out.

[IMG]https://s32.postimg.org/jpsuwnqtx/gparted_sdb.png[/IMG]

[IMG]https://s31.postimg.org/xaman19ij/gparted_sdb5.png[/IMG]

Can anyone point the way?

Thanks,

---

### Post by Impavidus on 2016-07-09
First enlarge sdb2, which is an extended partition and a container for sdb5.

---

### Post by Bucky Ball on 2016-07-09
As above, but you need to right click/unmount each before you can do anything. I suggest you do this from live boot media, i.e. the 'Try Ubuntu' option from the live install media you used to install. 

Point being that to unmount the extended partition and any partitions in it you need to make sure that the OS is not currently using any data from it. Using a live boot is the best way to ensure that.

---

### Post by Nutria on 2016-07-09
> **Bucky Ball said:**
> As above, but you need to right click/unmount each before you can do anything.

Already did that.  (There's no lock icon on sdb5.)  :D

> I suggest you do this from live boot media, i.e. the 'Try Ubuntu' option from the live install media you used to install.

This is a data disk, so I was able to umount it from my running system.

Thanks.

---

### Post by Nutria on 2016-07-09
> **Impavidus said:**
> First enlarge sdb2, which is an extended partition and a container for sdb5.

Why didn't I think of that??  :(

Anyway, it worked like a charm (except for the tons of 586 files stuffed in lost+found).  Thanks!!!

---

