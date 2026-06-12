---
title: "Mount Vista with user access"
date: 2007-07-10
forum: General Help
---

### Post by Tachyon on 2007-07-10
I'm dual booting Vista and Kubuntu (very happily, I might add).  Kubuntu mounts my Vista partition, but I can only access the public folders.  I want to access my user files under C:\Users\Ben\.

What do I put in fstab to mount Vista through my username and password?

---

### Post by HermanAB on 2007-07-10
You need a NTFS file system driver that can actually write.  The default NTFS driver can only read.  See the ntfs-3g project for a proper driver.

---

