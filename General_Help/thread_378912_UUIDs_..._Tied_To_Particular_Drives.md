---
title: "UUIDs ... Tied To Particular Drives?"
date: 2007-03-07
forum: General Help
---

### Post by rbil49 on 2007-03-07
Since the Ubuntu developers have decided to designate drives with UUIDs - "because it makes their lives easier" is the reason they say, I have a question about how easy it makes the end-users' lives.

Are these UUIDs tied to a particular hard drive? If I was to clone the hard drive onto another harddrive, which I do as a major backup measure and to move drives around to different boxes, will this break things because the UUID for one harddrive no longer applies to another harddrive? Or is the UUID immaterial to the actual hardware once it's assigned to a harddrive partition?

I can just imagine the chaos that would result if Grub or fstab is looking for a particular UUID that was created originally on one harddrive but now resides on a cloned image of that drive. 

Hope I'm wrong and this isn't going to be an issue.

Thanks. 

Cheers.

---

### Post by taurus on 2007-03-07
You don't have to use UUID for your partition in /etc/fstab.  You can use the old entry like /dev/hda1 if you want.  I also like to use the /dev/hda1 stuff instead of UUID and everything is running fine on my machines.

---

### Post by rbil49 on 2007-03-07
taurus, I'm aware of that. But I did an upgrade from dapper to edgy and found UUIDs in my grub and fstab. I've changed them all back to /dev's but I'm concerned that in future UUIDs will be forced on us. So, my question still stands .... does the use of UUIDs screwup when drives are cloned to new drives?

Cheers.

---

### Post by fragos on 2007-03-08
Each partition requires a unique UUID.  I seem to remember that getting one assigned is a simple process but I don't remember how its done.  I don't know if cloning a drive copies the UUID.

---

### Post by rbil49 on 2007-03-14
I'm assuming it reads it from the hard drive somehow? This command will give you the UUID for a particular partition (example) ...

sudo vol_id -u /dev/hda1

Cheers.

---

### Post by undecidable on 2007-03-14
Some notes:

1.  UUID gets created when the file sytem gets created.
2.  It is unique and does not depend on the hdd.  
3.   It is in the superblock  (try  tune2fs -l)
4.  so if you image a partition, then I believe the new partition will have the same UUID.
     (I have not checked this myself - post if for some reason this is not correct)
5.  If you are upgrading/cloning a hdd, this may be what you want.  
6.  If it is not what you want, you can change the UUID with  tune2fs -U <uuid>
	(check man for tune2fs - it can generate a new UUID for you or you can type one)
7.  I personally like UUIDs as those for existing paritions don't normally change after a repartition, whereas labels may, esp if you insert or delete a partition.  I believe this is the logic for Ub using them -   it generally makes life more robust for normal use.

---

### Post by dpm on 2007-03-25
> **undecidable said:**
> Some notes:

4.  so if you image a partition, then I believe the new partition will have the same UUID.
     (I have not checked this myself - post if for some reason this is not correct)


I just wanted to confirm that this is correct. Before any dist upgrade, I usually copy the partition to upgrade somwhere else with the live cd and gparted, so I always have a fallback OS I can use in case the upgrade failed or leaves me with an unusable system. The new copy always has the same UUID as the source, so I always generate a new UUID for the new partition after the copying process has finished.

```
tune2fs -U random /dev/hda1
```

This, for example, generates a new random UUID for /dev/hda1. Read the tune2fs man page for more options (and substitute hda1 for the partition you want to generate a new UUID for).

Cheers.

---

### Post by bulldog on 2007-03-25
To have a look at your UUID's ```
ls /dev/disk/by-uuid -lh
```

---

### Post by undecidable on 2007-03-25
> **desp said:**
> I just wanted to confirm that this is correct. Before any dist upgrade, I usually copy the partition to upgrade somwhere else with the live cd and gparted, so I always have a fallback OS I can use in case the upgrade failed or leaves me with an unusable system. The new copy always has the same UUID as the source, so I always generate a new UUID for the new partition after the copying process has finished.


desp

thanks for that confirmation, very handy to be certain.
btw, just in case anyone else is reading this, 
if you do change the uuid, and you end up needing to use that partition image,
and your grub uses uuids, you will need to edit grub menu also to include the newly generated uuid.

---

