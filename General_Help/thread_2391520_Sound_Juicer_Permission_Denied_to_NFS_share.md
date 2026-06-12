---
title: "Sound Juicer Permission Denied to NFS share"
date: 2018-05-10
forum: General Help
---

### Post by Jim_Valavanis on 2018-05-10
Hello again everybody,
Running Ubuntu 16.04 and trying to RIP CD's with Sound Juicer app to an NFS share.  I can write / delete / etc. to the NFS share via command line and other apps without issues.  But when using Sound Juicer and changing preferences to store in the NFS share, I get a permission denied error.

Any ideas what the problem might be?

TIA

---

### Post by TheFu on 2018-05-11
NFS usually doesn't allow root from remote systems.  Does Sound Juicer use root?
The NFS server - which OS is it?

---

