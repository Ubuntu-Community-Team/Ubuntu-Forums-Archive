---
title: "[SOLVED] vista partiton does not mount."
date: 2008-01-27
forum: General Help
---

### Post by Raccoon1400 on 2008-01-27
Ubuntu can't see my vista partition. The live CD can see it, but not mount it. Is there anything I can do?

---

### Post by taurus on 2008-01-27
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Raccoon1400 on 2008-01-27
duncan@duncan-laptop:~$ sudo fdisk -l
[sudo] password for duncan:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         667     5295104    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         668       12637    96149025    7  HPFS/NTFS
/dev/sda4           12638       19457    54781650    5  Extended
/dev/sda5           12638       19152    52331706   83  Linux
/dev/sda6           19153       19457     2449881   82  Linux swap / Solaris
duncan@duncan-laptop:~$

---

### Post by taurus on 2008-01-27
You want to mount both /dev/sda2 & /dev/sda3?

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda2 /media/sda3
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
sudo mount -t ntfs-3g /dev/sda3 /media/sda3
df -h
```

---

### Post by Raccoon1400 on 2008-01-27
only the third partition. the second is the recovery partition.

---

### Post by taurus on 2008-01-27
In that case, run

```

sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda3
sudo mount -t ntfs-3g /dev/sda3 /media/sda3
df -h

```

---

### Post by Raccoon1400 on 2008-01-27
I used that code and it said something about an unclean shutdown. I usually put vista into hibernate because it takes 1:30 min to boot up. So I boot into vista and shut it down completely, instead of hibernate. When I boot into ubuntu, both the recovery and OS partitions are now mounted.

---

### Post by costamatrix on 2008-03-10
Hi, i have the same problem on my Vista premium (hp dv2000)...

So i will not be able to access my vista partition when its in the hibernate mode?

---

