---
title: "No Permission to Shared Partition"
date: 2007-12-13
forum: General Help
---

### Post by RDonnelly on 2007-12-13
Hi everyone!  I recently just go my computer dual booting XP and Gutsy and I'm loving it.  However, I can't get it to work exactly how I'd like it to.  I made a FAT32 partition to hold all my music and videos, but I can't seem to access that in Ubuntu.  Whenever I try to put something in it, it tells me that I don't have permission.  Can anyone help me out?  I've looked in other topics and tried to get help but it hasn't worked.  Here's my fdisk read out and my fstab file:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65dc8805

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5228    41993878+   7  HPFS/NTFS
/dev/sda2            5229       10091    39062047+  83  Linux
/dev/sda3           10092       19457    75232395    5  Extended
/dev/sda5           10092       18845    70316473+   b  W95 FAT32
/dev/sda6           18846       19457     4915858+  82  Linux swap / Solaris

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                        0  0
# /dev/sda2
UUID=727972f7-7b8f-44ed-9e63-294f81f895af  /              ext3         defaults,errors=remount-ro      0  1
# /dev/sda1
UUID=787829B178296F56                      /media/sda1    ntfs         defaults,umask=007,gid=46       0  1
# /dev/sda5
UUID=DA52-6C88                             /media/sda5       vfat         defaults,utf8,umask=007,gid=46  0  1
# /dev/sda6
UUID=c4b00e5b-c758-4b5a-b96b-d45176c6c3b4  none           swap         sw                              0  0
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec                0  0
/dev/sda1                                  /media/sda1    ntfs         defaults                        0  0
/dev/sda5                                  /media/sda6    swap         defaults                        0  0
/dev/sda2                                  /media/sda2    ext3         defaults                        0  0
/dev/sdb1                                  /media/sdb1    vfat         defaults                        0  0
/dev/sda5                                  /media/sda5    vfat         defaults,uid=ryan,rw

```

---

### Post by floke on 2007-12-13
You have sda5 listed twice in your fstab - try changing this one - which is activating it as a swap file!

/dev/sda5                                  /media/sda6    swap         defaults                        0  0

---

