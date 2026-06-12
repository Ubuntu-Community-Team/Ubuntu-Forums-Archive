---
title: "Is it safe to increase partition size of BOOT with gparted?"
date: 2008-06-24
forum: General Help
---

### Post by JustAnotherVagueAnon on 2008-06-24
I want to increase the size of my boot partition by giving it space from my main ubuntu partition. Is it safe to resize without losing data? I have only a small amount of my main partition used.

---

### Post by VMC on 2008-06-24
> **JustAnotherVagueAnon said:**
> I want to increase the size of my boot partition by giving it space from my main ubuntu partition. Is it safe to resize without losing data? I have only a small amount of my main partition used.

For one thing you will have to do that off-line with maybe the livecd. There was someone earlier that had issue with just that problem.

So you have just one linux partition and an a swap partition? If yo do that, then the UUID will change. Post the output from a Terminal this:

```
sudo fdisk -l
```

---

### Post by ryanhaigh on 2008-06-24
Changing the size of your partitions will leave your system in an unbootables state as the UUIDs of the partitions will change and these are what grub/fstab and other things use to identify the disk to boot from. You can of course update grub, fstab and whatever else with the new UUIDs once you have resized the partitions.

[http://ubuntuforums.org/showthread.php?t=771358](http://ubuntuforums.org/showthread.php?t=771358)

EDIT: Forgot to mention that I have never had any problems with data loss due to resizing a partition with gparted. Also for VMC it sounds like the OP has a separate /boot and / partition.

---

### Post by louieb on 2008-06-24
From my own experience 98 or 99 time out of a 100 things will go just fine. 
Backup first.
McFalls' Maxim
					No degree of acceptance can ever change the facts.
					Translation: You may come to terms with being screwed, but nevertheless you're still screwed.

---

### Post by JustAnotherVagueAnon on 2008-06-25
> **VMC said:**
> For one thing you will have to do that off-line with maybe the livecd. There was someone earlier that had issue with just that problem.

So you have just one linux partition and an a swap partition? If yo do that, then the UUID will change. Post the output from a Terminal this:

```
sudo fdisk -l
```

Here's my output:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfd9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38391   308375676    b  W95 FAT32
/dev/sda2           38392       38913     4192965   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19190   154139719+   7  HPFS/NTFS
/dev/sdb2           19191       19197       56227+  83  Linux
/dev/sdb3           29263       30401     9149017+   7  HPFS/NTFS
/dev/sdb4           19198       29262    80847112+   5  Extended
/dev/sdb5           19198       19445     1992028+  82  Linux swap / Solaris
/dev/sdb6           19446       29262    78855021   83  Linux

Partition table entries are not in disk order


```

I want to give /dev/sdb2 space from /dev/sdb6

---

### Post by VMC on 2008-06-25
This could end up a nightmare if done wrong. I didn't realize you had seperate root partition.
sdb6 is inside an Extended partition. If you follow "ryanhaigh" link that is the best way to do this. I would advise to somehow backup everything. 

Just follow ryanhaigh's link and boot with livecd and go from there.

---

