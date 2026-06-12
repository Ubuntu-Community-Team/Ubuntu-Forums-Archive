---
title: "ntfs USB read only?"
date: 2006-11-14
forum: General Help
---

### Post by zombie_killer on 2006-11-14
I'd like to backup my storage drive to another drive via USB.  Both the storage and the external are NTFS.  I've mounted my storage drive using the ubuntuguide method, but when I try to write to do anything on the external, it says it is read only, and I can't even change permissions on it.

Any thoughts?

Also, I wouldn't mind reformatting the external into ext3 if I have to, but I'd still rather be able to write to NTFS external drives.

---

### Post by testube_babies on 2006-11-14
NTFS write capability is not default in Linux.  Here's one way to enable it, but be warned that writing to NTFS from linux is risky business:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

