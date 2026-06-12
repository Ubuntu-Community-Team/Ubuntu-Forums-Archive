---
title: "[SOLVED] No swap, fstab has wrong info"
date: 2008-03-19
forum: General Help
---

### Post by sgardne on 2008-03-19
I just recently noticed that my swap partition is not functioning. I'm not really sure what to do.

/etc/fstab contains:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cb8fb88e-4f9e-45cd-b826-466130419dfc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8cf4dbd6-b121-48eb-be1f-3c91d9fdf051 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# Beginning of the block added by the VMware software
.host:/                 /mnt/hgfs               vmhgfs  defaults,ttl=5     0 0
# End of the block added by the VMware software
```

I don't actually have a /dev/sda5. My swap is located on /dev/sda2 How do I make fstab mount the right one?

fdisk shows me this:
```
$fdisk -l

Disk /dev/sda: 107.3 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ae306

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12793   102759741   83  Linux
/dev/sda2           12794       13054     2096482+  82  Linux swap / Solaris
```

---

### Post by sgardne on 2008-03-19
So, if anyone cares, the fix was to replace the section reading: ```

# /dev/sda5
UUID=8cf4dbd6-b121-48eb-be1f-3c91d9fdf051 none            swap    sw              0       0

```
with:```

# /dev/sda2
/dev/sda2       none    swap    sw      0       0

```
If anyone can see anything I might've messed up with that, please let me know. Thanks!

---

### Post by bodhi.zazen on 2008-03-19
List your partitions with this command :

```
sudo blkid
```

This will list them with uuid

update this line in fstab :

> UUID=8cf4dbd6-b121-48eb-be1f-3c91d9fdf051 none            swap    sw              0       0

with the correct uuid # from the first command.

Edit fstab with :

```
gksu gedit /etc/fstab
```

change gksu to kdesu if you use kde.

---

### Post by sgardne on 2008-03-19
Hey, thanks. There's another tool for my bag. =)

---

### Post by Neilor on 2008-05-07
Thanks for this also... I think this is a bug in the Heron upgrade.. I saw the same thing when I re-enabled the swap using the GUI it worked but on reboot it was disabled again.

On looking at the fstab I found 2 entries.. one the original post Heron upgrade that had a wrong UUID.

At least I'm back to normal operating speeds... thought I was running Vista there for a while :)

---

### Post by bodhi.zazen on 2008-05-07
> **Neilor said:**
> Thanks for this also... I think this is a bug in the Heron upgrade.. I saw the same thing when I re-enabled the swap using the GUI it worked but on reboot it was disabled again.

On looking at the fstab I found 2 entries.. one the original post Heron upgrade that had a wrong UUID.

At least I'm back to normal operating speeds... thought I was running Vista there for a while :)

The "problem" is that as a part of installation most distro's format swap. When this happens the UUID changes, thus you need to update /etc/fstab.

---

