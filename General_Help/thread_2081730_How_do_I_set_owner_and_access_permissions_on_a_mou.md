---
title: "How do I set owner and access permissions on a mounted partition?"
date: 2012-11-07
forum: General Help
---

### Post by s.v.z on 2012-11-07
Hi! I have an NTFS partition mounted at /home/svz/data. The default owner of this directory and all its subdirectories is root. How can I change the owner and the access permissions for the entire partition or its subdirs?

I tried to use `sudo chown` and `sudo chmod` but this results in nothing happening.

---

### Post by Lars Noodén on 2012-11-07
NTFS is defective and cannot handle regular permissions.  

You'll have to mount the partition using the uid and gid options.  This problem with NTFS comes up often.  Here are some details on setting it up:
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by cbennett926 on 2012-11-07
ASFIK All drives and directories are root within Ubuntu

---

### Post by s.v.z on 2012-11-07
> **Lars Noodén said:**
> NTFS is defective and cannot handle regular permissions.  

You'll have to mount the partition using the uid and gid options.  This problem with NTFS comes up often.  Here are some details on setting it up:
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Thanks, that's a really good how to.

---

