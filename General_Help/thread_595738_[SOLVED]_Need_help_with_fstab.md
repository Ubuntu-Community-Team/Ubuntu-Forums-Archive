---
title: "[SOLVED] Need help with fstab"
date: 2007-10-29
forum: General Help
---

### Post by HXn on 2007-10-29
1) I'm trying to auto-mount three disks, however every time I restart, the partitions change (e.g., sda1 changes to sdb1).  I need them mounted to specific folders so I have the naming scheme intact.
```

# 100GB
/dev/sda1       /media/downloads        ext3    defaults        0       0
# 120GB
/dev/sdb1       /media/other    ext3    defaults        0       0
# 1TB
/dev/sdd1       /media/videos   ext3    defaults        0       0

```

2) I need to auto-mount network shares:
```

//hxn-desktop-win/w     /media/_wares   cifs    ro      0       0
//hxn-desktop-win/u     /media/_audio   cifs    ro      0       0

```
This doesn't appear to do anything.  I've also tried *smbfs*, but it didn't work either.

Full fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda1
UUID=58c83b7d-0022-482e-8e71-89cf01927a1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=760e2352-b5c7-4398-98d9-3a3ca0d517c8 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# 100GB
/dev/sda1       /media/downloads        ext3    defaults        0       0
# 120GB
/dev/sdb1       /media/other    ext3    defaults        0       0
# 1TB
/dev/sdd1       /media/videos   ext3    defaults        0       0

//hxn-desktop-win/w     /media/_wares   cifs    ro      0       0
//hxn-desktop-win/u     /media/_audio   cifs    ro      0       0

```

Thanks

---

### Post by odinfromvalhalla on 2007-10-29
If it does not work via fstab just add your smbmount lines to /etc/rc.local and they will be executed on boot

this might help u:

[http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab](http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab)

---

### Post by HXn on 2007-10-29
Thanks odin, that should work.

**I still need help with #1 above.**

---

### Post by taurus on 2007-10-29
Are those external or internal drives?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by vanadium on 2007-10-29
It are probably external drives that should not be mounted using /etc/fstab. Normally, internal drives do not swap identities, and if they do, then you can circumvent it by using UUIDS instead of device names to mount the drives.

---

### Post by HXn on 2007-10-29
Yes, they are internal drives.  How do I mount with the UUID? I've never done that before.

```

~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4940493f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8918    71633803+  83  Linux
/dev/sda2            8919        9039      971932+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8741

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x763d6ff4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12161    97683201   83  Linux

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeac0eac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14593   117218241   83  Linux

```

As stated above, I need the mounts as follows:
1TB -> /media/videos
120GB -> /media/other
100GB -> /media/downloads

---

### Post by CoolDreamZ on 2007-10-29
See this thread for help with permanently mounting samba shares:

[HOWTO: Mount SMB shares]("http://ubuntuforums.org/showthread.php?t=280473")

---

### Post by CoolDreamZ on 2007-10-29
This may help with your other problem:

[http://manual.sidux.com/en/part-uuid-en.htm]("http://manual.sidux.com/en/part-uuid-en.htm")

---

### Post by HXn on 2007-10-29
That works, thanks everyone.

---

