---
title: "mounting gvfs (raid 0)"
date: 2012-12-09
forum: General Help
---

### Post by 3246251196 on 2012-12-09
I run two "identical" hdds in a RAID 0 config. Simply: How can I mount a partition within this raid 0?

Of course Ubuntu loads up as usual, fstab shows:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_eccbjfbfgj_Volume0p3 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_eccbjfbfgj_Volume0p4 none            swap    sw              0       0
```But, there are times when I want to mount my NTFS(Windows) partition. This can be done easily with nautilus and the mount is available within ~/.gvfs, but what command is used? I have tried to search with no success.

There is gvfs-mount:
```
/etc$ gvfs-mount E06698A566987E4A
Error mounting location: volume doesn't implement mount
/etc$ gvfs-mount /dev/mapper/isw_eccbjfbfgj_Volume0p2
Error mounting location: volume doesn't implement mount
```What I am doing wrong?

Thank you.

---

### Post by 3246251196 on 2012-12-10
> **3246251196 said:**
> I run two "identical" hdds in a RAID 0 config. Simply: How can I mount a partition within this raid 0?

Of course Ubuntu loads up as usual, fstab shows:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_eccbjfbfgj_Volume0p3 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_eccbjfbfgj_Volume0p4 none            swap    sw              0       0
```But, there are times when I want to mount my NTFS(Windows) partition. This can be done easily with nautilus and the mount is available within ~/.gvfs, but what command is used? I have tried to search with no success.

There is gvfs-mount:
```
/etc$ gvfs-mount E06698A566987E4A
Error mounting location: volume doesn't implement mount
/etc$ gvfs-mount /dev/mapper/isw_eccbjfbfgj_Volume0p2
Error mounting location: volume doesn't implement mount
```What I am doing wrong?

Thank you.

Dang, why can no one ever answer my questions...

---

### Post by 3246251196 on 2012-12-11
Hi, I am sorry to reply to this a third time:

But does no one really not know what command is essentially being executed behind the scenes when I mount my xGB device on the Nautilus screen that then makes it automatically mounted and available in ~./gvfs.

Thanks.

---

### Post by 3246251196 on 2012-12-12
```
gvfs-mount smb://computer/share/
```
```
gvfs-mount -u smb://computer/share
```

---

