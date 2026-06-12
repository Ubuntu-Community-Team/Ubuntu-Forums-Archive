---
title: "Format HDD or USB drive to Mac OS Extended"
date: 2013-10-14
forum: General Help
---

### Post by adam17 on 2013-10-14
Hi,

Is there any software that will allow me to format a USB drive or HDD to MAC OS Extended file system? 

I had a look in the disk utility and couldnt find it. 

I am running Ubuntu 12.04LTS

Thanks In advance.

Adam

---

### Post by lukeiamyourfather on 2013-10-14
If you install hfsprogs you can do it from GParted. Though I wouldn't recommend doing that. If the disk will be used with a Mac just format it with a Mac. If the disk will be used with Linux format it as a Linux native file system like ext4. If it needs to work with both know that there will be limitations and risk of losing or corrupting the data.

---

