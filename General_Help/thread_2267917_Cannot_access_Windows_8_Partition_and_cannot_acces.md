---
title: "Cannot access Windows 8 Partition and cannot access partition"
date: 2015-03-04
forum: General Help
---

### Post by ryan144 on 2015-03-04
Hey. I am having trouble mounting a Windows 8 partition from Ubuntu
It is caused by Windows 8 "fast startup" as outlined in [https://wiki.archlinux.org/index.php/NTFS-3G](https://wiki.archlinux.org/index.php/NTFS-3G)

```

The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdc1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

Unfortunately, the hard drive on which the windows partition is installed is dying. It is no longer possible to boot to the OS, so I cannot turn fast startup off. 

How do I force the partition to mount as read/write?
I want to erase files (via shred), so potential damage to the files is irrelevant.

Thanks

---

### Post by sandyd on 2015-03-04
> **ryan144 said:**
> Hey. I am having trouble mounting a Windows 8 partition from Ubuntu
It is caused by Windows 8 "fast startup" as outlined in [https://wiki.archlinux.org/index.php/NTFS-3G](https://wiki.archlinux.org/index.php/NTFS-3G)

```

The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdc1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

Unfortunately, the hard drive on which the windows partition is installed is dying. It is no longer possible to boot to the OS, so I cannot turn fast startup off. 

How do I force the partition to mount as read/write?
I want to erase files (via shred), so potential damage to the files is irrelevant.

Thanks

Simply shred the whole partition
Disclaimer: THIS IS NOT RECOVERABLE. Make sure that the partition is correct when typing.
```

sudo shred -n 5 -v /dev/sdc1
```

---

