---
title: "Access ext3 from Windows or NTFS from Linux"
date: 2008-05-28
forum: General Help
---

### Post by sulusulu on 2008-05-28
I have a laptop with Kubuntu currently installed and I want to dual boot with Winows XP. I want to set it so that I have one large data partition that will be used by both Widows and Linux for file storage.  Would it be better to format the partition in ext3 and use [fs-driver]("http://www.fs-driver.org/index.html") to access it in Windows or format it in NTFS and access it using ntfs-3g in Linux? Thanks! :)

---

### Post by karl_eller on 2008-05-28
I'd be inclined to make it an NTFS partition. The various Ubuntu 8.04 versions (Ubuntu, Xubuntu, Kubuntu, etc) all have the NTFS-3G driver enabled by default, and I haven't had any issues with using Ubuntu writing to NTFS partitions.

The NTFS-3G driver is quite stable, but I'm not sure if the same goes for the various Windows Ext3 drivers.

Eller

---

### Post by russo.mic on 2008-05-28
The fs-driver works great under windows.  Never had a problem!

Russo

---

