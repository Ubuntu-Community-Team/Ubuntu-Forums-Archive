---
title: "Will Ubuntu 20.04 get encryption update?"
date: 2020-06-01
forum: General Help
---

### Post by bdarbro on 2020-06-01
Focal came with ZFS 0.8.3, and encryption is working, but 0.8.4 was released with significant performance increases for ZFS encryption.  I see those changes were backported to Groovy's 0.8.3, but haven't seen them either backported or upgraded in 20.04 yet.  Will those changes be coming to us anytime soon or at all?  I tried building the updated packages from Groovy, but they refuse to install over dependencies.

Thanks.

---

### Post by CatKiller on 2020-06-01
I don't know specifically about that, but security fixes and "significant" bugfixes are backported. ZFS is a big feature for Ubuntu, so if there's a big improvement to be had it seems likely to be that they'll pursue backporting it.

---

### Post by Yellow Pasque on 2020-06-02
The 0.8.4 update was just uploaded to Groovy proposed a few hours ago. Hopefully, focal will not be too far behind:
[https://bugs.launchpad.net/ubuntu/focal/+source/zfs-linux/+bug/1881107](https://bugs.launchpad.net/ubuntu/focal/+source/zfs-linux/+bug/1881107)

---

### Post by bdarbro on 2020-06-04
focal-proposed just got the update, backported to 0.8.3.

[FONT=lucida console][/FONT][FONT=courier new]libzfs2linux/focal-proposed             0.8.3-1ubuntu12.1  amd64  [upgradable  from:  0.8.3-1ubuntu12]
zfs-dkms/focal-proposed,focal-proposed  0.8.3-1ubuntu12.1  all    [upgradable  from:  0.8.3-1ubuntu12]
zfs-initramfs/focal-proposed            0.8.3-1ubuntu12.1  amd64  [upgradable  from:  0.8.3-1ubuntu12]
zfs-zed/focal-proposed                  0.8.3-1ubuntu12.1  amd64  [upgradable  from:  0.8.3-1ubuntu12]
zfsutils-linux/focal-proposed           0.8.3-1ubuntu12.1  amd64  [upgradable  from:  0.8.3-1ubuntu12][/FONT]

zfs-linux (0.8.3-1ubuntu12.1) focal; urgency=medium

  * Backport AES-GCM performance accelleration (LP: #1881107)
   - backport of upstream zfs commit 31b160f0a6c673c8f926233af2ed6d5354808393
     ("ICP: Improve AES-GCM performance").
     tests on a memory backed pool show performance improvements of ~15-22%
     for AES-CCM writes, ~17-20% AES-CCM reads, 34-36% AES-GCM writes and
     ~79-80% AES-GCM reads.

 -- Colin Ian King <colin.king@canonical.com>  Tue, 28 May 2020 11:54:33 +0100

---

