---
title: "New wubi install won't mount file system, aborts startup"
date: 2007-10-21
forum: General Help
---

### Post by bga123 on 2007-10-21
Hi,

I just installed Wubi Ubuntu 7.10 and after rebooting chose the ubuntu boot option from the Windows boot options. It started the X system and then tossed an error "Invalid file system type ntfs cannot be mounted on /. because it is not a full-functional Linux file system. Please choose a different file system, such as ext2."

Any ideas? I thought it was going to mount the image file it created on the hard disk that would have been a valid file system.

---

### Post by RandomSkratch on 2007-10-21
I encountered the same error on my desktop.  It could be because the 7.10 installer is still in Alpha.. I'm sticking with 7.04 until it's a little more developed, even though I can't wait!

---

### Post by bga123 on 2007-10-21
Misery loves company. Thanks for your feedback.

---

### Post by ago on 2007-10-21
Use the latest alpha (347 at the moment) and make sure that you run chkdsk from windows before that. If you still have the same issue, post here /var/log/syslog (or look for errors related to ntfs)

---

