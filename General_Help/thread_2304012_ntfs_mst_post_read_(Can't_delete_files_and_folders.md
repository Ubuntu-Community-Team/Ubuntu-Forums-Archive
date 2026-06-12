---
title: "ntfs_mst_post_read (Can't delete files and folders from ntfs partition)"
date: 2015-11-23
forum: General Help
---

### Post by zeusys on 2015-11-23
Hi
I want to delete some files and directories from and external hard disk. The filesystem of hard disk in NTFS.
But I can't delete them, and I see the following error as the output of journalctl  command


```
Nov 23 22:01:33 homelinux1 ntfs-3g[5974]: ntfs_mst_post_read_fixup_warn: magic: 0x00000000  size: 4096   usa_ofs: 0  usa_count: 65535: Invalid argument
Nov 23 22:01:33 homelinux1 ntfs-3g[5974]: Index buffer (VCN 0x0) of directory inode 311734 has a size (24) differing from the directory specified size (4096).

```


Please guide me how I can fix this

---

### Post by matt_symes on 2015-11-23
Hi

Have you tried running *chkdsk* from a Windows machine ? 

It is a Windows filing system so i would use their tools.

Kind regards

---

