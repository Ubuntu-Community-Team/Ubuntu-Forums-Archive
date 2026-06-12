---
title: "Mount FreeBSD UFS2 filesystem fails"
date: 2016-05-08
forum: General Help
---

### Post by SVMartin80 on 2016-05-08
All,

I have attached an external USB harddrive to my FreeNAS 9.10 box (based on FreeBSD 10). On the harddrive I have created a partition table, a partition and a filesystem, using the following documentation:

[https://www.freebsd.org/doc/handbook/disks-adding.html](https://www.freebsd.org/doc/handbook/disks-adding.html)

Next, I copy some files to the external harddrive, unmount the drive and connect it to my Ubuntu 16.04 workstation. There I mount it using:

mount -r -t ufs -o ufstype=ufs2  /dev/sdb1 /media/martin/

This command fails, dmesg says:

ufs: failed to set blocksize

I have tried several other things that I found using google, didn't work. But I believe the above steps should have worked.

How to setup/mount a UFS2 filesystem properly?

Thanks in advance!

---

