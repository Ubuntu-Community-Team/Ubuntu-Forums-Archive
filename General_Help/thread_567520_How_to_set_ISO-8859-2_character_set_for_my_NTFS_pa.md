---
title: "How to set ISO-8859-2 character set for my NTFS partitions?"
date: 2007-10-04
forum: General Help
---

### Post by garferi on 2007-10-04
Hi!
I use accentuated folders and files in my NTFS drives, but Ubuntu can't show its.
I would like to use ISO-8859-2 character set for my mounted NTFS drives, but I couldn't found the mount informations in /etc/fstab
#
proc /proc proc defaults 0 0
/media/host/wubi/disks/system.virtual.disk / ext3 loop,sync 0 1
/media/host/wubi/disks/home.virtual.disk /home ext3 loop,sync 0 2
/media/host/wubi/disks/swap.virtual.disk none swap sw 0 0

How can I set my NTFS drives to show all folders which have accents?
Thanks!

---

### Post by ago on 2007-10-05
> **garferi said:**
> Hi!
I use accentuated folders and files in my NTFS drives, but Ubuntu can't show its.
I would like to use ISO-8859-2 character set for my mounted NTFS drives, but I couldn't found the mount informations in /etc/fstab
#
proc /proc proc defaults 0 0
/media/host/wubi/disks/system.virtual.disk / ext3 loop,sync 0 1
/media/host/wubi/disks/home.virtual.disk /home ext3 loop,sync 0 2
/media/host/wubi/disks/swap.virtual.disk none swap sw 0 0

How can I set my NTFS drives to show all folders which have accents?
Thanks!

To change the settings of /media/host is difficult at the moment. You can specify the charset when mounting OTHER partitions in /etc/fstab

---

