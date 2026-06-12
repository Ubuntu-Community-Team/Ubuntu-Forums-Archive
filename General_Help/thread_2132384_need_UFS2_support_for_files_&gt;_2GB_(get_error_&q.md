---
title: "need UFS2 support for files &gt; 2GB (get error &quot;File too large&quot; writing to UFS2)"
date: 2013-04-04
forum: General Help
---

### Post by pemu27 on 2013-04-04
Dear experts,

Strange scenario, however I hope to get some help here: to be able to write back files to a corrupted disk formatted by my Panasonic Viera TV I need help on write support for files larger than 2GB on an UFS2 file system.

I have already compiled a new kernel with UFS r/w support (instructions from [http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/](http://ghantoos.org/2009/04/04/mounting-ufs-in-readwrite-under-linux/)).
I am able to mount this file system in r/w mode (mount -t ufs -o ufstype=ufs2 ...).

Nevertheless, when I try to "cp" or "dd" a large file with around 5GB  to this rw-mounted file system it stops at a size of 2147483647 and gives the error "cp: writing `/mnt/ufs01/109_00.tts': File too large". The dd gives a similar error.

It is no problem at all to write the large 5GB file to an ext4 file system. So it must have to do something with the UFS write support in the kernel of Ubuntu. I am using Ubuntu 10 with kernel 2.6.32.

Many thanks,
Peter

---

