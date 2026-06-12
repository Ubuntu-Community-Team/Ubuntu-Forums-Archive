---
title: "[Hardy] Not all NTFS partitions listed under 'Media'"
date: 2008-05-14
forum: General Help
---

### Post by CrazyArcher on 2008-05-14
Hello

I have a dual boot system (Kubuntu 8.04/XP), and when I try to access my NTFS partitions, it only shows me the one located on the same physical HDD with the ext3 partition. I have another HDD with several NTFS partitions, and I can't see them in Kubuntu. I have no trouble in accessing any NTFS partitions from WinXP, neither had trouble when I was running Gutsy (there were mounting problems, but that's another issue), and when I was installing Hardy all existing partitions were seen in the partition manager as well.

Possible causes/solutions? :confused:

---

### Post by pointone on 2008-05-14
Post your /etc/fstab file, please.

---

### Post by CrazyArcher on 2008-05-14
Thank you for your responce. Here you are:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=7e85808a-6189-43c8-8622-a2c7164d918e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=588d54ae-c44e-44b2-baae-01126d4d120b none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

As we can see, it doesn't list the partitions named sda1, sda2 and sda3 (they exist).
One more remark that may help. At the beginning, when Ubuntu starts, before the splash screen I see a glimpse of console messages, and there are a couple of reported errors there. Maybe there are hints in the booting log?

---

