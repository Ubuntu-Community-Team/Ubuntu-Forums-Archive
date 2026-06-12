---
title: "Extended attributes"
date: 2013-06-04
forum: General Help
---

### Post by Mr.Sykkoh on 2013-06-04
Hi my fellow ubuntu linux users!

Im doing some school project where i have a tons of latex files and pictures stored on my pc, the problem is that the filenames doesn't really describe anything of the files.
So i came up with a solution to start adding meta data on thoose files to fill out a description of them. 
I added user_xattr in /etc/fstab

```

# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/fedora-root /               ext4, user_xattr,    errors=remount-ro 0       1
/dev/mapper/cryptswap1 none swap sw 0 0

```

Looks good to me?
When im checking up mount :
```

mount | grep xattr/dev/mapper/fedora-root on / type ext4 (rw,user_xattr)

```

Still looks good to me..
But when im trying to add an attribute, it fails
```

sudo setfattr -n user.name -v "data" ./data.meta
setfattr: ./data.meta: Operationen er ikke understøttet

```
It returns "Operation is not supported" - how come?

Anyone having any clue ?

Thankes in advance!
// Mr.Sykkox

---

