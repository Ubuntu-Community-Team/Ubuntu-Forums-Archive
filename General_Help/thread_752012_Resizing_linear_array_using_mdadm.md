---
title: "Resizing linear array using mdadm"
date: 2008-04-11
forum: General Help
---

### Post by peitschie on 2008-04-11
Firstly, I managed to work around this problem by installing evms-ncurses and using that to grow the array through a pretty gui... having said that, I would like to know how to do this using mdadm because evms is no longer supported!

So, does anyone know (or can point me to something that will tell me) how to grow a linear array?  I've been trying to add a drive into a linear array but it keeps reporting "invalid argument".  The command I have been using is:

```

mdadm --grow /dev/md0 --add /dev/hdb1

```

The output of fdisk -l /dev/hdb1 is
```

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd9635f9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   83  Linux

```

---

