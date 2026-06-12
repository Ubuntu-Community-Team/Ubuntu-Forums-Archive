---
title: "Swap file error message?"
date: 2007-08-19
forum: General Help
---

### Post by Sparky222B on 2007-08-19
During boot without quite and splash on, I see a message about "swap file" [fail]. What's going on here? Why would the swap fail to mount? I haven't noticed any problems yet, but is this an issue?

---

### Post by kellemes on 2007-08-19
> **Sparky222B said:**
> During boot without quite and splash on, I see a message about "swap file" [fail]. What's going on here? Why would the swap fail to mount? I haven't noticed any problems yet, but is this an issue?

The message doesn't say the mounting of your swappartition failed..
Maybe it a message to confirm you're using swappartition instead of swapfile.

---

### Post by taurus on 2007-08-19
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
free
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Sparky222B on 2007-08-19
```

sparky@SparkyPC:~$ free
             total       used       free     shared    buffers     cached
Mem:       3116068    1480348    1635720          0      62236    1116552
-/+ buffers/cache:     301560    2814508
Swap:      2931852          0    2931852

```

```

sparky@SparkyPC:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21522   172875433+   7  HPFS/NTFS
/dev/sda2           21523       24427    23334412+  83  Linux
/dev/sda3           24428       24792     2931862+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdb5               2       24321   195350368+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19929   160079661    7  HPFS/NTFS

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                            0  0
# /dev/sda2
UUID=2c90cfe1-1680-4cf6-9bec-0fd9217457c9  /               ext3         defaults,errors=remount-ro          0  1
# /dev/sda1
UUID=138020C16A18B8B9                      /media/sda1     ntfs         defaults,nls=utf8,umask=007,gid=46  0  1
# /dev/sdb5
UUID=F8F0B88DF0B8541A                      /media/sdb5     ntfs         defaults,nls=utf8,umask=007,gid=46  0  1
# /dev/sda3
UUID=24dcba3f-9474-40c6-aebe-9b1a1ea2de30  none            swap         sw                                  0  0
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto                         0  0
/dev/scd1                                  /media/cdrom1   udf,iso9660  user,noauto                         0  0
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto                      0  0

```

This is interesting, though. I'm showing 0% swap usage. See attachment.

---

### Post by taurus on 2007-08-19
> **Sparky222B said:**
> ```

sparky@SparkyPC:~$ free
             total       used       free     shared    buffers     cached
Mem:       3116068    1480348    1635720          0      62236    1116552
-/+ buffers/cache:     301560    2814508
**Swap:      2931852          0    2931852**

```

This is interesting, though. I'm showing 0% swap usage. See attachment.

Looks like your swap partition, /dev/sda3, mounted just fine.  You want the system to use the actual RAM since it would be much faster than the swap partition.

---

### Post by Sparky222B on 2007-08-19
Oh, so the swap partition is like overflow RAM..? Sorry, I know that's a dipshit noob question.

---

