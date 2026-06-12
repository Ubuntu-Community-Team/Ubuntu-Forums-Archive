---
title: "Mounting Problems"
date: 2007-02-19
forum: General Help
---

### Post by jdkc4d on 2007-02-19
I'm not really sure if this is the right place for this question, but here goes.

Running Ubuntu 6.1 (Edgy Eft) from inside VMware Workstation
I am attempting to mount an initrd file, I did the following (as root):

```
cp initrd initrd.gz
gunzip initrd
mkdir work
mount -o loop initrd work
```

To which mount replys, "you must specity the filesystem type"
I have tried ext2, and mount then replys:

"wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or other error"

I have looked in both /etc/filesystems and /proc/filesystems, and both locations are empty.

Any help would be appreciated.

---

