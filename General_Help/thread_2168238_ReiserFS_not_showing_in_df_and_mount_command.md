---
title: "ReiserFS not showing in df and mount command"
date: 2013-08-17
forum: General Help
---

### Post by bibble235 on 2013-08-17
Hi,

Title says most of it.

I have a ReiserFS filesystem which I have created from an ex-RAID (in case it is important) and it does not show up when I type mount or df -h. I also notice there is no mount.reiserfs. It does not really bother me but I am curious.

Thanks,
Iain

---

### Post by tgalati4 on 2013-08-17
I believe support for ReiserFS was dropped recently.  I have the ReiserFS utilities on an older Linux Mint system:


tgalati4@tpad-Gloria7 ~ $ apropos ReiserFS
debugreiserfs (8)    - The debugging tool for the ReiserFS filesystem.
filesystems (5)      - Linux file-system types: minix, ext, ext2, ext3, Reiserfs, XFS, JFS, xia, msdos, umsdos, vfat, proc, nfs, iso9660, hpfs, sysv, smb, ncpfs
fs (5)               - Linux file-system types: minix, ext, ext2, ext3, Reiserfs, XFS, JFS, xia, msdos, umsdos, vfat, proc, nfs, iso9660, hpfs, sysv, smb, ncpfs
fsck.reiserfs (8)    - The checking tool for the ReiserFS filesystem.
mkfs.reiserfs (8)    - The create tool for the Linux ReiserFS filesystem.
mkreiserfs (8)       - The create tool for the Linux ReiserFS filesystem.
reiserfsck (8)       - The checking tool for the ReiserFS filesystem.
reiserfstune (8)     - The tuning tool for the ReiserFS filesystem.
resize_reiserfs (8)  - resizer tool for the ReiserFS filesystem

Check the repositories for ReiserFS tools:

```
apt-cache search ReiserFS
```

---

### Post by bibble235 on 2013-08-18
Sorry this was my own fault. I do not know how but I failed to noticed this was not mount and I had copied to the mount point not the disk.

---

