---
title: "Can no longer write to Windows partitions from Ubuntu 18.04"
date: 2019-01-03
forum: General Help
---

### Post by klundermann on 2019-01-03
I dual-boot Ubuntu 18.04 and Windows 10.  For years I've been reading  and writing to my NTFS HDD partitions and FAT- and FAT32-formated USB  drives.  Lately, though I can still read Windows partitions from Ubuntu  18.04, I am unable to write.

For what it's worth, here's /etc/fstab:```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=3221e8c2-eb9e-4cc7-8d7e-5f522b044bea /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=80CE-E957  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=141e5e5c-d48d-4cab-9809-1a6d5dd791fc none            swap    sw              0       0
```


Would anyone have any suggestions as to how to enable writing or at least begin diagnosing the problem?

---

### Post by ajgreeny on 2019-01-03
I suspect a Windows update may have re-enabled fast-start, ie hibernation instead of shutdown of your Windows OS.

This however, usually means the Windows the partitions are not available to Ubuntu in any way and can not be mounted, though you say you can read the files which I would not expect to be the case; can you confirm this is so for all the Windows partitions, or is it just those that are other filesystems than ntfs?

---

### Post by klundermann on 2019-01-05
I was unclear.

The only Windows partition on my HDD is formatted  as NTFS.  I have just confirmed that I can read it from Ubuntu but  cannot write to it.

The FAT partitions I referred to were USB  drives.  While I was under the impression that I could no longer write  to any FAT (could be FAT32) USB drives, I have found one that I can  write to.

---

### Post by klundermann on 2019-01-08
Update: I have exactly the same problem on another laptop, which also dual-boots Ubuntu (18.10, this time) and Windows 10.

---

