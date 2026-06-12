---
title: "Resizing a swap partition?"
date: 2008-06-30
forum: General Help
---

### Post by pjkoczan on 2008-06-30
Hi all,

Is there any way to resize a SWAP partition on a disk, more or less "on the fly."

By "on the fly" I mean short of reinstalling or completely formatting a disk, and preferably at least somewhat automated (i.e. manual reboots are fine, but running fdisk or parted for that many machines would be a nightmare). I've seen that adding a swap file is an option, but resizing the partition itself would be optimal.

---

### Post by VMC on 2008-06-30
You can use gparted. Click on the swap partition, then swap-off, and resize, then swap-on. That might have problems depending where the Swap is positioned.

Once you change Swap size I think its UUID will change, then you need to make corrections in fstab.

Can you output this:

```
sudo fdisk -l
```

---

### Post by drs305 on 2008-06-30
Also there have been some users reporting problems with hibernation that may have been related to improper identification of the swap partition. If the UUID changes, you may want to check the following:

```
sudo blkid && cat /etc/initramfs-tools/conf.d/resume
```
If they don't match:
```

sudo update-initramfs -u

```

---

### Post by pjkoczan on 2008-07-01
> **VMC said:**
> You can use gparted. Click on the swap partition, then swap-off, and resize, then swap-on. That might have problems depending where the Swap is positioned.

Once you change Swap size I think its UUID will change, then you need to make corrections in fstab.

Thanks, this works, but it's not quite what I'm looking for. I'm researching this for work, and we might have to do this for ~100 machines (possibly more in the future), so I'm looking for a way to automate it. Is there a way to do this from the CLI?

> Can you output this:

```
sudo fdisk -l
```

```
[root@ator] ~ $ /sbin/fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         131     1052226   83  Linux
/dev/sda2             132        1436    10482412+  83  Linux
/dev/sda3            1437        1958     4192965   83  Linux
/dev/sda4            1959        9729    62420557+   5  Extended
/dev/sda5            1959        2219     2096451   82  Linux swap / Solaris
/dev/sda6            2220        2350     1052226   83  Linux
/dev/sda7            2351        2481     1052226   83  Linux
/dev/sda8            2482        9729    58219528+  83  Linux

```

/dev/sda5 is the swap partition, and I'm a bit worried about it encroaching on the other partitions (/tmp, a cache for our networked file system, and a lot of scratch space).

Thanks again.

---

### Post by VMC on 2008-07-01
You might consider a Swap file rather than a partition. Read this tutorial for better explanation:

[http://ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file](http://ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file)

---

### Post by hardyn on 2008-07-01
as i have read the current suspend handler does not work with swap files.  that would have to be swapped out too... and that would require a kernel rebuild.

that said, ubuntu mainly targeted at being a desktop OS should really look at dynamic swap file as apposed to a swap partition... seems to make better sence in this contect.

---

