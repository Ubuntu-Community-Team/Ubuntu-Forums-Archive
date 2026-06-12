---
title: "how to create new partition"
date: 2006-12-29
forum: General Help
---

### Post by mdsmedia on 2006-12-29
I'm trying to follow Aysiu's guide to create a /Home partition

I have the following partitions:

hda1 Windows ntfs
hda2 Linux ext3
hda3 data FAT32
hda4 swap

In gparted I've resized hda1 and can resize hda2 to allow say 5-10Gb free space.

When I try to create a new partition it tells me I can only have 4 primary partitions. In other words, the 4 partitions I have are primary.

What I'd like to do is create a new partition for /home. Can I do it inside gparted?

---

### Post by NeoLithium on 2006-12-29
Swap doesn't need to be a primary partition, you can delete that, create an extended partition within the space, and then put the swap partition inside there, same space, leftoever primary slot for you.

---

### Post by mdsmedia on 2006-12-29
Wonderful :)

Thanks. I'll try that.

---

