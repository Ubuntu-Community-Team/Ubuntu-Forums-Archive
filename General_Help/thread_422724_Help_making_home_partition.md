---
title: "Help making /home partition?"
date: 2007-04-25
forum: General Help
---

### Post by pndragon on 2007-04-25
I have read the tutorial at [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome"). The problem is that GParted only wants to resize the boot partition.

This is output of fdisk -l:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32       12161    97434225    5  Extended
/dev/hda5              32         314     2273166   82  Linux swap / Solaris
/dev/hda6             315       12161    95160996   8e  Linux LVM

```

Any help would be greatly appreciated.

---

### Post by pndragon on 2007-04-25
I have answered my own question as far as why GParted or QtParted is of no help in my present dilemma. Neither of these programs operate on lvm partitions.

Can anyone tell me how to carve a separate /home partition out of a lvm partition?

---

### Post by asipi on 2007-04-26
why u need LVM? not so reasonable in homeuse unless e.g u editing videos and time to time u need to extend your diskspace...

anyway for new home insert a new disk :) make the partition, mount it anywhere e.g /mnt, copy all your things from the actual /home to the mounted partition on /mnt, edit your fstab to mount the new partition into /home, remove the content of the old /home then mount the new one (of coure umount first from /mnt)

it is recommended to do all of this logged in as root an not with sudo commands

that's all ;)

---

