---
title: "can't fit file over 4.3gb on flash drive"
date: 2023-02-18
forum: General Help
---

### Post by cmacc77 on 2023-02-18
i read to format with ntfs or exfat, but these options are grayed out in disks.  any ideas how to fix?

screen shot:  [https://imgur.com/FzHPhYK](https://imgur.com/FzHPhYK)

---

### Post by TheFu on 2023-02-18
Have you installed the support packages for those file systems?  I'd use synaptic to search for the correct package or 
```
$ apt search exfat
```

However, if this flash drive will only be used with Linux, use **f2fs** instead. This is a native Linux file system designed for flash drives, but without journaling.  f2fs = Flash Friendly File system.  it has been around long enough to be trusted and is very fast - sometimes faster than ext4. [https://www.phoronix.com/news/Linux-5.14-File-Systems](https://www.phoronix.com/news/Linux-5.14-File-Systems) has more about the performance of the popular Linux file systems.

---

### Post by cmacc77 on 2023-02-19
worked, TY

---

### Post by cmacc77 on 2023-02-19
asdfasdfasdf

---

### Post by mIk3_08 on 2023-02-19
> **cmacc77 said:**
> worked, TY
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

