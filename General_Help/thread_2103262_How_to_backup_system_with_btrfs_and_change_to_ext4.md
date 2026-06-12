---
title: "How to backup system with btrfs and change to ext4"
date: 2013-01-09
forum: General Help
---

### Post by rado3105 on 2013-01-09
Hi after installing system with btrfs system is very slow. Is possible to backup running system, or any offline backup tool for btrfs(dont think this is possible). And change to ext4? thanks

---

### Post by dcstar on 2013-01-10
> **rado3105 said:**
> Hi after installing system with btrfs system is very slow. Is possible to backup running system, or any offline backup tool for btrfs(dont think this is possible). And change to ext4? thanks

You cannot "change" any partition type. You have to create a new partition and copy all existing files onto it - ensuring that all permissions etc. are identical and then changing /etc/fstab to use the new partition.

It might be possible without too many issues, but it may be a lot easier just to do a new install on a fresh EXT4 partition.

---

### Post by rado3105 on 2013-01-10
> **dcstar said:**
> You cannot "change" any partition type. You have to create a new partition and copy all existing files onto it - ensuring that all permissions etc. are identical and then changing /etc/fstab to use the new partition.

It might be possible without too many issues, but it may be a lot easier just to do a new install on a fresh EXT4 partition.

could you help how to copy everything? I have / on /dev/sda1, MBR Is /dev/sda

---

