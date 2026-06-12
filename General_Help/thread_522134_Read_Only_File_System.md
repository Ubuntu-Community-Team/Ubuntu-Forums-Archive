---
title: "Read Only File System"
date: 2007-08-10
forum: General Help
---

### Post by itamari on 2007-08-10
I installed nfts-3g to mount my windows partition.
after installation it worked great untill the next reboot.

since then it mounts my / as read-only.
I can't edit fstab / mtab can't do nothing...
how can I fix edit fstab when my FS is mounted as ro ?

Example:
When trying 'sudo mount -a' I get:

unable to open fuse lock file
Failed to open /etc/mtab: Read-Only file system
FUSE mount point Falied

---

### Post by streeto on 2007-08-10
Could you please post your /etc/fstab?

Try to boot into recovery mode, or to use a live CD to mount the root rw.

-st.

---

### Post by anagor on 2007-08-10
you can try to remount / to be writable by issuing:

sudo mount -o remount,rw /

But be aware that ubuntu by default mounts root as read-only if there were errors on it,
so maybe it will be better if you boot from liveCD and check root for errors first.
also here is my optins in fstab that mounts ntfs partition:

what_to_mount   where_to_mount     ntfs    defaults,nls=utf8,umask=007,gid=46  0  1

maybe this will help?

---

