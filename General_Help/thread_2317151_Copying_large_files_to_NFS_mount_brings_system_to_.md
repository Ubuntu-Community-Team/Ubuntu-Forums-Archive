---
title: "Copying large files to NFS mount brings system to a halt"
date: 2016-03-13
forum: General Help
---

### Post by artelius on 2016-03-13
Hi,


I've seen ancient threads and bug reports about this sort of problem, but hardly any recent reports; seems like the problem doesn't affect many people any more? Copying a large file (several GB) to an NFS mount erratically causes the system to slow down and eventually freeze completely.

Adding 'sync' to the mount options seems to prevent the problem but transfers become ridiculously slow. I have tried changing rsize and wsize to no avail. Is there anything else I can do?

I'm using Trusty 14.04. The server is running up-to-date Arch.

Thanks

---

