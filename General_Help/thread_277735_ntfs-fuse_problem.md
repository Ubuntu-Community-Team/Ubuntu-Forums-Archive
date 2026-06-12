---
title: "ntfs-fuse problem"
date: 2006-10-15
forum: General Help
---

### Post by Zalbor on 2006-10-15
I started mounting my NTFS partitions with ntfs-fuse a few days ago, for write support (I'm aware of the risk in that).
I'm using the greek version of Windows, so some directories (even system ones) have greek names. For example, "&#932;&#945; &#941;&#947;&#947;&#961;&#945;&#966;&#940; &#956;&#959;&#965;" for "My Documents".
The problem is that although sometimes ntfs-fuse seems to mount the partitions with the correct character encoding to see these directories, sometimes it doesn't and as a result I can't access them.
As far as I can tell, it seems to happen randomly. The mount options I've specified in /etc/fstab are: "auto,gid=1002,umask=0007" (1002 is the group for write access to ntfs). The nls option, which I used with the normal driver, doesn't seem to exist in ntfs-fuse, and "man ntfsmount" doesn't seem to inform me of a similar one.
How can I set it to mount with a specific encoding? The one I used before was utf8.

---

### Post by Zalbor on 2006-10-16
Anyone? I tried to add the option "locale=el_GR.utf8" but it still doesn't work sometimes.

---

