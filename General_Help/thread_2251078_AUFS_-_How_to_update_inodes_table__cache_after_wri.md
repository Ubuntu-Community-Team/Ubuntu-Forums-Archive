---
title: "AUFS - How to update inodes table / cache after writing to an underlying branch?"
date: 2014-11-01
forum: General Help
---

### Post by f1sheyes on 2014-11-01
Hi all,

Have spent the last few hours reading the aufs man pages but still not clear on how to fix this.
I have 3 writeable branches that make one large aufs filesystem. Unfortunately one of the writeable branches was amended directly and as such the unionfs inode table is incorrect / confused. (It does not show some files that are present in the underlying branch). My question is how do I force aufs to resync / rescan ?

Looking at the mount options I now appreciate I should not have set "udba=none".
Example of the current mount options # mount -t aufs -o br=/mnt/disk1=rw:/mnt/disk2=rw:/mnt/disk3=rw,sum,create=mfs,clean_plink reveal /mnt/aufs

Thanks in advance.

---

