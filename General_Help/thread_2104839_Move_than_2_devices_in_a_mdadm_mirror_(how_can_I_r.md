---
title: "Move than 2 devices in a mdadm mirror (how can I remove one)"
date: 2013-01-14
forum: General Help
---

### Post by matmbl on 2013-01-14
Hi All,

i'm running a mirror (RAID1) across 3 physical disks (yes, that means 3 copies of the data) and I'd like to remove disk and reuse it for other things.

I've failed and stop one disk, removed it from the array but now I get a degraded array report on reboot. How can I tell the array I will only have 2 device in there from now on (or do I have to re-create the array!?)

Thanks

Matt

---

### Post by matmbl on 2013-01-15
Oh, that was easy (once I figured out grow also means shrink).

Anyway, for the solution as I said I "failed" and "removed" the disk I wanted to take out of the array, then issues the command

mdadm --grow /dev/md2 --raid-devices=2

and instantly the jobs done, looking at /proc/mdstat, /etc/mdadm/mdadm.conf and the superblocks of the devices (see mdadm --examine /dev/sd?) all seems well and the array is now just 2 devices. Now should I convert to RAID5 with my spare ;-)

---

