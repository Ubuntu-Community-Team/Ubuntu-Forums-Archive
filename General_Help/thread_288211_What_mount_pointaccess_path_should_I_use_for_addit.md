---
title: "What mount point/access path should I use for additional disks?"
date: 2006-10-29
forum: General Help
---

### Post by Schammy on 2006-10-29
I have Ubuntu installed on a 40gig IDE drive.  I have another IDE and 2 SATA drives that I want to mount and use too.

I'm confused about the access path that I should choose...

-- Can I use the same path for more than one disk?
-- Can I mount to any existing folder in the file system?
-- Is there and ideal way to best manage the mount points for several disks like this?  I do want to share all of the drive space on my LAN.

Thanks!

---

### Post by aysiu on 2006-10-29
> **Schammy said:**
> 
-- Can I use the same path for more than one disk? No. If one drive is mounted to /media/storage, no other drive can be simultaneously mounted to /media/storage. You would have to something like /media/storage1 and /media/storage2 > -- Can I mount to any existing folder in the file system? Quite the contrary, the existing folders are usually in use. You would want to mount to a new folder you create. Exceptions are when you want to move an existing folder to a new partition, for example:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) > -- Is there and ideal way to best manage the mount points for several disks like this? Ideal is whatever works for you. Really, you can mount to anywhere within the filesystem. Some people mount to /home/*username*/folder. Others mount completely outside in something like /storage or /documents. Still others prefer to do it within the /media directory in something like /media/storage or /media/documents.

---

### Post by Schammy on 2006-10-29
Thanks for the quick reponse.  Now I'm gonna mount up!

---

