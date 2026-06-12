---
title: "Windows Recovery Partition"
date: 2007-08-17
forum: General Help
---

### Post by Kver on 2007-08-17
Hello; I've installed Ubuntu over a finicky vista installation, and I'm having trouble accessing the partition.

The install was don't thinking there were two HD's, however later we found that it was one HD with 2 partitions.

Specifically, the computer I installed Ubuntu on had 2 partitions, a Vista partition, and a recovery partition (oddly with XP installed). The recovery partition was the partition being used, because the Vista side was fubar. The recovery partition accumulated photos that we need to get at, and Ubuntu can't seem to mount the recovery partition (with XP and the photos).

Thank you for any advice,
Ken.

---

### Post by merlinus on 2007-08-17
Post results of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin

---

