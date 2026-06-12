---
title: "USB write cache"
date: 2006-11-07
forum: General Help
---

### Post by poncenby on 2006-11-07
Would anyone happen to know how to disable the write cache for USB devices?
to achieve two things:
1) if disconnected midway through a transfer all writes but the interrupted one are written and not lost
2) minimal/no delay when umounting the device cleanly

many thanks

poncenby

---

### Post by Ramses de Norre on 2006-11-07
I think you can achieve this by mounting them with the sync option.

---

### Post by pitkali on 2006-11-07
> **poncenby said:**
> 
1) if disconnected midway through a transfer all writes but the interrupted one are written and not lost
This is actually often the case with cache enabled. Cache is periodically written out to the drive - not only during unmounting.

---

### Post by jpkotta on 2006-11-07
I'm not sure if you can disable it.  I remember looking at an article about the VFS (virtual file system) a long time ago and it sounded like everything was cached.  But as always, there are tweaks.   I found [this]("http://www.gentoo.org/doc/en/articles/l-afig-p8.xml"); look at the "bdflush" stuff at the bottom.  It's a start, anyway.

---

### Post by jpkotta on 2006-11-07
> **Ramses de Norre said:**
> I think you can achieve this by mounting them with the sync option.

From the mount manpage:
>        -o     Options are specified with a -o flag followed by a comma separated string of options.   Some  of  these
              options  are  only  useful when they appear in the /etc/fstab file.  The following options apply to any
              file system that is being mounted (but not every file system actually honors  them  -  e.g.,  the  sync
              option today has effect only for ext2, ext3 and ufs):


---

