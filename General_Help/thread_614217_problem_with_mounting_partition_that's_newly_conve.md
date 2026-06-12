---
title: "problem with mounting partition that's newly converted to NTFS"
date: 2007-11-15
forum: General Help
---

### Post by initialxy on 2007-11-15
hello everyone,
i just converted a partition of mine from FAT32 to NTFS after realizing the fact that gutsy gibbon has the ability to read AND write NTFS now. but the problem is that after the conversion, this partition (/dev/sda7) is not mounted at startup. i was able to mount it by
```
mount /dev/sda7 /media/sda7
```
that works perfectly. but it just doesn't mount at start up.
can anyone please help?
is it possible to reset fstab or something like that without reinstall the whole OS?
thanks!

---

### Post by taurus on 2007-11-15
Can you post your /etc/fstab?  Make sure the entry for /dev/sda7 is correct since you converted it from vfat to ntfs.

```
cat /etc/fstab
```

---

