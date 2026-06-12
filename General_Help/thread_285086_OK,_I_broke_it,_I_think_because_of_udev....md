---
title: "OK, I broke it, I think because of udev..."
date: 2006-10-26
forum: General Help
---

### Post by mrcpu on 2006-10-26
Wanting to play with Xen, I downloaded the xen 3.0.3 source distribution and installed it.  Went pretty painlessly, edit menu.lst, rebooted, and all is kind of well.

My main disk mounts fine on /, and swap is there, but attempts
to mount the other disks like sdb1 and sdc1 result in "Device busy" or "already mounted" messages, even though they are not.

Some of them are ext3 and reiserfs, so it can' tbe a missing file system driver.

/dev has an entry for each disk, sda through sdd, with a sda1, sdb1, sdc1, sdd1 entry.

The xen source install did update my kernel to 2.6.16.29-xen, but networking works and such, I think it's udev related.

---

