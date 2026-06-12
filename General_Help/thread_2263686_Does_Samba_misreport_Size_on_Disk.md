---
title: "Does Samba misreport Size on Disk?"
date: 2015-02-02
forum: General Help
---

### Post by kayot2 on 2015-02-02
I'm worried that I'm loosing a ton of file space. I have a Ubuntu Server 14.04LTS with Samba 4. I'm using a BTRFS with 5 4TB drives. When I do a file query in Windows 8.1, the size on disk is huge compared to the file itself.

[ATTACH=CONFIG]259669[/ATTACH]

```
root@server:/media/Data# btrfs fi df ArchiveData, single: total=8.00MiB, used=0.00B
Data, RAID5: total=12.69TiB, used=12.31TiB
System, single: total=4.00MiB, used=0.00B
System, RAID5: total=12.75MiB, used=784.00KiB
Metadata, single: total=8.00MiB, used=0.00B
Metadata, RAID5: total=19.00GiB, used=16.05GiB
GlobalReserve, single: total=512.00MiB, used=0.00B
```

```
root@server:/media/Data# df
Filesystem       1K-blocks        Used  Available Use% Mounted on
/dev/sdg1         98776676     2203460   91532576   3% /
none                     4           0          4   0% /sys/fs/cgroup
udev               8185644           8    8185636   1% /dev
tmpfs              1639168        8640    1630528   1% /run
none                  5120           0       5120   0% /run/lock
none               8195820           0    8195820   0% /run/shm
none                102400           0     102400   0% /run/user
/dev/sdf1        312568640   192152980  120415660  62% /media/Square
/dev/sdh1        961300776    63384252  897900140   7% /media/Temp
/dev/sda       19534994616 13234325700 2886251004  83% /media/Data
```

It's like each cluster is 1mb. I set the cluster size to 4096b during BTRFS creation. I'm wondering if perhaps samba is simply reporting inaccurate information. I need three commands to confirm my suspicion.

One command to get total file space on the array.
One command to get total file space used by all the files on the array.
One command to get total free space on the array.

The best solution would be a command that shows "Size on Disk" in the Linux console.

---

### Post by jones7 on 2015-06-01
Hmm here is a workaround,

1. Edit smb.conf and add followings:
[global]
allocation roundup size = 4096

2. Restart samba.

---

