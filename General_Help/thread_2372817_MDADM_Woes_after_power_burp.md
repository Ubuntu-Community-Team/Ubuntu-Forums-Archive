---
title: "MDADM Woes after power burp"
date: 2017-09-29
forum: General Help
---

### Post by goatcow on 2017-09-29
half of my disk set powered off due to a weird power hiccup (don't ask, it was foolish) - it looks like linux didn't freeze the array fast enough.  Now i can't seem to get the array to start up.  any help?

```
root@basestar22:~/bin# mdadm --assemble --force /dev/md9 /dev/mapper/cryptr6b1  /dev/mapper/cryptr6d1  /dev/mapper/cryptr6f1  /dev/mapper/cryptr6h1  /dev/mapper/cryptr6j1 /dev/mapper/cryptr6a1  /dev/mapper/cryptr6c1  /dev/mapper/cryptr6e1  /dev/mapper/cryptr6g1  /dev/mapper/cryptr6i1 -v
mdadm: looking for devices for /dev/md9
mdadm: /dev/mapper/cryptr6b1 is identified as a member of /dev/md9, slot 1.
mdadm: /dev/mapper/cryptr6d1 is identified as a member of /dev/md9, slot 3.
mdadm: /dev/mapper/cryptr6f1 is identified as a member of /dev/md9, slot 5.
mdadm: /dev/mapper/cryptr6h1 is identified as a member of /dev/md9, slot 7.
mdadm: /dev/mapper/cryptr6j1 is identified as a member of /dev/md9, slot 9.
mdadm: /dev/mapper/cryptr6a1 is identified as a member of /dev/md9, slot 0.
mdadm: /dev/mapper/cryptr6c1 is identified as a member of /dev/md9, slot 2.
mdadm: /dev/mapper/cryptr6e1 is identified as a member of /dev/md9, slot 4.
mdadm: /dev/mapper/cryptr6g1 is identified as a member of /dev/md9, slot 6.
mdadm: /dev/mapper/cryptr6i1 is identified as a member of /dev/md9, slot 8.
mdadm: added /dev/mapper/cryptr6b1 to /dev/md9 as 1
mdadm: added /dev/mapper/cryptr6c1 to /dev/md9 as 2
mdadm: added /dev/mapper/cryptr6d1 to /dev/md9 as 3
mdadm: added /dev/mapper/cryptr6e1 to /dev/md9 as 4
mdadm: added /dev/mapper/cryptr6f1 to /dev/md9 as 5
mdadm: added /dev/mapper/cryptr6g1 to /dev/md9 as 6 (possibly out of date)
mdadm: added /dev/mapper/cryptr6h1 to /dev/md9 as 7 (possibly out of date)
mdadm: added /dev/mapper/cryptr6i1 to /dev/md9 as 8 (possibly out of date)
mdadm: added /dev/mapper/cryptr6j1 to /dev/md9 as 9 (possibly out of date)
mdadm: added /dev/mapper/cryptr6a1 to /dev/md9 as 0
mdadm: /dev/md9 assembled from 6 drives - not enough to start the array.

```
```

root@basestar22:~/bin# mdadm --examine /dev/mapper/cryptr6* |  egrep 'Event|/dev/mapper'
/dev/mapper/cryptr6a1:
         Events : 6089276
/dev/mapper/cryptr6b1:
         Events : 6089276
/dev/mapper/cryptr6c1:
         Events : 6089276
/dev/mapper/cryptr6d1:
         Events : 6089276
/dev/mapper/cryptr6e1:
         Events : 6089276
/dev/mapper/cryptr6f1:
         Events : 6089276
/dev/mapper/cryptr6g1:
         Events : 6089112
/dev/mapper/cryptr6h1:
         Events : 6089112
/dev/mapper/cryptr6i1:
         Events : 6089112
/dev/mapper/cryptr6j1:
         Events : 6089112

```

---

### Post by wildmanne39 on 2017-09-29
*Thread moved to **General Help for better support**.*

---

### Post by konveksitas on 2017-09-30
[COLOR=#000000]*i would suggest you try it out in live session first before installing. that way you can painlessly see if all your things work in linux.*[/COLOR]

---

### Post by TheFu on 2017-09-30
If there are encrypted storage underlying the array storage, I'd wipe the mdadm array and start over from scratch using backups to restore any data.

Corrupt encrypted storage has very few methods to recover besides restoring from backups.

---

### Post by goatcow on 2017-10-02
The storage doesn't appear corrupt or any issues with the luks.

It appears from the second code snippet that the software raid continued to write events to 1/2 the disks, even though the other half was powered off.  So the software raid is out of sync.

---

### Post by TheFu on 2017-10-03
In theory, if 1 out of 2 RAID1 disks was lost, then the whole point of RAID1 is for the other disk to continue. It should be storing data, getting farther and farther out of sync.   But is appears you aren't running RAID1 - can't really tell from the data provided.  At this point, you should have solved this by either adding in a replacement disk and everything should be rebuilding (or already done) 
or
wiped the array completely, rebuilt it, and should be restoring from backups.

We only know what you've posted here. We need to **see** commands that provide information (mdadm --details) and (cryptsetup LUKSdump) before making any concrete suggestions.  We really don't want to assume anything and it is common for posters to leave off critical information which the data gathering information would include.  Please show your work, so we can help.

---

### Post by goatcow on 2017-10-03
It's a raid6 array, so i can't just add in a replacement disk, when half-ish the disks are being excluded.  obviously if this was 2 or less disks i'd just re-add them and be on my merry way.

madam --details is a invalid command.  madam --detail requires a assembled raid device - which from the above assemble command you can see i can't do.  the drives decrypt fine - so just ignore that they are encrypted.  

the problem is that half the disks have 6089276 events and the other half have 6089112. trying to assemble, without specifying the devices yields the same results.  the raid metadata is intact/the disks are discovered, but enough devices are behind that it can't start.


```

root@basestar22:~# mdadm --assemble --force /dev/md9 -vvv 2>&1| egrep -v 'no RAID'
mdadm: looking for devices for /dev/md9
mdadm: /dev/dm-11 is identified as a member of /dev/md9, slot 9.
mdadm: /dev/dm-10 is identified as a member of /dev/md9, slot 8.
mdadm: /dev/dm-9 is identified as a member of /dev/md9, slot 7.
mdadm: /dev/dm-8 is identified as a member of /dev/md9, slot 6.
mdadm: /dev/dm-7 is identified as a member of /dev/md9, slot 5.
mdadm: /dev/dm-6 is identified as a member of /dev/md9, slot 4.
mdadm: /dev/dm-5 is identified as a member of /dev/md9, slot 3.
mdadm: /dev/dm-4 is identified as a member of /dev/md9, slot 2.
mdadm: /dev/dm-3 is identified as a member of /dev/md9, slot 1.
mdadm: /dev/dm-2 is identified as a member of /dev/md9, slot 0.
mdadm: added /dev/dm-3 to /dev/md9 as 1
mdadm: added /dev/dm-4 to /dev/md9 as 2
mdadm: added /dev/dm-5 to /dev/md9 as 3
mdadm: added /dev/dm-6 to /dev/md9 as 4
mdadm: added /dev/dm-7 to /dev/md9 as 5
mdadm: added /dev/dm-8 to /dev/md9 as 6 (possibly out of date)
mdadm: added /dev/dm-9 to /dev/md9 as 7 (possibly out of date)
mdadm: added /dev/dm-10 to /dev/md9 as 8 (possibly out of date)
mdadm: added /dev/dm-11 to /dev/md9 as 9 (possibly out of date)
mdadm: added /dev/dm-2 to /dev/md9 as 0
mdadm: /dev/md9 assembled from 6 drives - not enough to start the array.

```


So really i guess i'm looking for is a way to roll back events?  From 6089276 -> 6089112

---

