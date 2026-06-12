---
title: "How To Access Mountable Drives from SFTP Account"
date: 2014-05-03
forum: General Help
---

### Post by chiques on 2014-05-03
Hello Community,
I have a total of 3 hard drives on my server. Only 1 of them is set to mount during boot, the other two I mount on demand. What I'm finding is that after I mount them in ssh I still do not have permissions to access the drives in sftp.

It sounds like a permission problem but I'm unable to determine what users should be in what groups.


Thanks for any help.

---

### Post by ajgreeny on 2014-05-03
How are these drive partitions formatted; ntfs, ext4, other filesystem?

---

### Post by chiques on 2014-05-03
> **ajgreeny said:**
> How are these drive partitions formatted; ntfs, ext4, other filesystem?


```
/dev/sdc1  fuseblk   xxx xxx xxx  68% /media/2TB
/dev/sdc2  fuseblk   xxx xxx xxx  33% /media/1TB
```


Good question. I'm not sure what I did here.

---

### Post by ajgreeny on 2014-05-05
Not sure either, though a search of fuseblk suggests it is just the way ntfs is detected by the system.  However, I do not have any ntfs disks on which to investigate this, so can't really help.

---

