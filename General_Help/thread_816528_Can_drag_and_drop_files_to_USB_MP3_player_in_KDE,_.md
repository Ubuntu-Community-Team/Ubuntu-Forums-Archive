---
title: "Can drag and drop files to USB MP3 player in KDE, but not Gnome."
date: 2008-06-02
forum: General Help
---

### Post by heyho on 2008-06-02
As per title, I am able to load up my MP3 player using KDE, but if I try the same in Gnome, I get the "you do not have permission..." message, even though permissions appear to be correct.

I had this trouble a while back, and it appeared to right itself in the end for no apparent reason, but since a firmware upgrade on the player, it has returned!  KDE is fine, as is XP.

Don't know if this is of any relevance, but it doesn't look right to me!

```
paul@paul-laptop:~$ sudo fdisk -l
[sudo] password for paul:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2f92bb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8011    64348326    7  HPFS/NTFS
/dev/sda2            8012       14318    50660977+  83  Linux
/dev/sda3           14319       14593     2208937+   5  Extended
/dev/sda5           14319       14593     2208906   82  Linux swap / Solaris

Disk /dev/sdb: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders
Units = cylinders of 504 * 512 = 258048 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     1543921     3808821   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(1543920, 4, 5)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(3808820, 4, 35)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      334702     4176028   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(334701, 3, 51)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(4176027, 2, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     3710083     7551409   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(3710082, 2, 26)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(7551408, 0, 25)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     7216720  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(7216719, 2, 8)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
paul@paul-laptop:~$ 




```

---

### Post by heyho on 2008-06-04
Can anybody tell me what that output means?

---

### Post by yaknowwat on 2008-06-04
Well the output is not related to your mp3 player.

But the output you posted is suspicious because what its saying is that the partitions data block mapping is off or incorrect. Just as easily it could be all the non-Linux partitions messing up the way things are read.

your mp3 issue is more than likely a gnome setting issue i have no experience with mp3 players in gnome so i cannot help with that.

---

### Post by heyho on 2008-06-04
Thanks for the reply.

I am not overly knowledgable about the way linux labels discs, but I thought that this was my HD:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2f92bb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8011    64348326    7  HPFS/NTFS
/dev/sda2            8012       14318    50660977+  83  Linux
/dev/sda3           14319       14593     2208937+   5  Extended
/dev/sda5           14319       14593     2208906   82  Linux swap / Solaris
```

And this was my USB MP3 player:

```
Disk /dev/sdb: 262 MB, 262144000 bytes
9 heads, 56 sectors/track, 1015 cylinders
Units = cylinders of 504 * 512 = 258048 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     1543921     3808821   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(1543920, 4, 5)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(3808820, 4, 35)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      334702     4176028   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(334701, 3, 51)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(4176027, 2, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     3710083     7551409   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(3710082, 2, 26)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(7551408, 0, 25)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     7216720  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(7216719, 2, 8)
Partition 4 does not end on cylinder boundary.




```

I thought that purely because it's the only other drive on the system, and it was the right size (256mb), and the default firmware splits it automatically into 3 folders after a format.  I'll keep digging and learning, and hopefully get to the root (pun intended) of this!

---

### Post by yaknowwat on 2008-06-05
Actually your correct i must of misread that i do that sometimes if i only glance over something.

Have you recently tried formatting a partition of your mp3 player?

The more than likely issue is the partition are corrupt this can happen if a partition is altered while at least one of the partition on the device are mounted sometimes thing corrupt by themselves.  

If i had to guess i would say the partitions on your mp3 player are corrupt.

Partition corruption would cause issues with gnome because, gnome has a load of checks built in to be safer on hardware.

If it were a lack of format modules then i'd think that kde would not work either.

---

### Post by heyho on 2008-06-05
Thanks again for your reply.  The fact that you mention gnome being a bit picky would make sense.  I'll keep digging, but it's not as if I'm stuck - can always use KDE.

---

