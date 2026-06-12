---
title: "How to auto mount my NTFS partition in Ubuntu"
date: 2008-06-20
forum: General Help
---

### Post by El Chicken DIablo on 2008-06-20
Hello

I've just installed Ubuntu Hardy Heron on my PC, but I have a small problem with it. I've got the hard drive partitioned into two parts, one for the OS and one for the files. But the problem is that the partition for the files isn't auto mounted when I start the machine and therefor any shortcuts I have to contet on that disk can't be used unless I mount the hard drive first. The partition is using the NTFS file system and any help on getting to auto mount the disk on startup would be great. :)

---

### Post by drs305 on 2008-06-20
Here is an easy-to-use summary of how to automount ntfs partitions using ntfs-config:
[http://ubuntuforums.org/showthread.php?t=785263]("http://ubuntuforums.org/showthread.php?t=785263")

Essentially install ntfs-config and follow the directions upon opening it.
```

sudo aptitude install ntfs-config
```

Once installed it's available under the "System Tools" menu.

---

