---
title: "Bad superblock on ext3 filesystem?"
date: 2007-10-03
forum: General Help
---

### Post by Githlar on 2007-10-03
I ran Gparted to add a DOS partition to my drive so I could play some of those really old games that I love. However, during the partitioning, something went horribly wrong. OK, here's what my disk looked like before:

Partition 1: Primary: ext3 55G /dev/sdb1
Partition 2: Primary: extended 445G
[
Partition 3: Logical: swap 1.5G
Partition 4: Logical: fat32 443.5G
]

OK, so I shrank partition 2 and shifted it to the end of the disk. I then used the 10gigs or so of free space to create a partition for FreeDOS.

But,  for some reason or another, it messed up my first partition - which shouldn't have been touched.

Now, GRUB comes up and tells me "Error 15." I booted the Gparted LiveCD and tried to use e2fsck to check the file system, and it tells me that there is a bad superblock and to try to use another superblock.

What does this mean?

I can't mount the partition because of this problem, so I can't transfer any of my needed files.

---

