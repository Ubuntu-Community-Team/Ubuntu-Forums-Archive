---
title: "ddrescue with USB Enclosure"
date: 2020-07-29
forum: General Help
---

### Post by hdrecover on 2020-07-29
[COLOR=#242729][FONT=Arial]I'm about to start a recovery with ddrescue and was wondering if i'm on the right path with these steps. I'm planning to[/FONT][/COLOR]

[LIST]
[*]boot via ubuntu live usb and use ddrescue
[*]disable automount in ubuntu
[*]connect the new target drive via SATA on my computer
[*]connect the old failing drive via USB enclosure
[*]run ddrescue with a first pass to quickly recover the easy sectors and then run a second pass
[/LIST]
```
[COLOR=#242729][FONT=Arial]
ddrescue -f -n /dev/sdb /dev/sdc rescue.log[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
ddrescue -d -f -r3 /dev/sdb /dev/sdc rescue.log
[/FONT][/COLOR]
```
[COLOR=#242729][FONT=Arial]I'm wondering[/FONT][/COLOR]

[LIST=1]
[*]Where do i write the log file (map file) if the ubuntu live usb does not have persistent storage and the other disks are unmounted? Can I also write that to the new target disk? How big is the log file typically?
[*]I read it's not a good idea to connect the hard drive to a USB enclosure? What alternative do I have though if I only have one SATA connection?
[*]If I had to choose, is it better to have the new drive in the SATA port and the failing drive in the enclosure or vice versa?
[*]Do I have to ensure the drives are not mounted before running ddrescue?
[*]Do I have to check if the disk sector sizes are the same and pass any parameters to ddrescue if they're not?
[/LIST]
[COLOR=#242729][FONT=Arial]Any help would be appreciated. Thanks in advance[/FONT][/COLOR]

---

### Post by dinkidonk on 2020-07-29
1) Either to the live USB stick or to memory.
2) The USB enclosure may be faulty, that's why the recommendation is to take the drive out of it.
3) I would rather not have any drive in an enclosure where a drive has failed - just to be sure. But if I had to, I would put the bad drive in SATA and the good in USB.
4) Yes, when mounted the system (and what not) may access the drives and you do not want that since you operate at block level.
5) They are the same unless one drive is rediculously older than the other. Since ~2010 most HDD's (but not SSD's) use "Advanced Format" which is 4KiB sectors.

Good luck with the rescue!

---

