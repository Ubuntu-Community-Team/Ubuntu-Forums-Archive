---
title: "Hard drive limit (with RAID 6 system)"
date: 2008-05-14
forum: General Help
---

### Post by beertastic on 2008-05-14
i've jsut ordered a new box.
standard spec (dual core, 2Gb RAM)
but I've added a 3ware RAID card and 6 x 1Tb drives.

My plan is to use a RAID 6 setup and have one uber large drive with which to share all media to my house.

My question is:
Does Ubunutu have a 2Tb drive limit as XP appears to?

Basically, can I use this box to host one large drive..?

Thoughts?

---

### Post by fjgaude on 2008-05-14
It would be best to do a google on ext3 and see what file and drive size limits are. My memory is not so good, but I think standard ext3 has an 8TB file limit and I can't remember what the drive limit is, it is large.

---

### Post by talz13 on 2008-05-14
ext3 does support drives (arrays) that large, but you could always try any of the number of other filesystems, like XFS if you're working with large files.

From wikipedia:

[http://en.wikipedia.org/wiki/Ext3#Size_limits](http://en.wikipedia.org/wiki/Ext3#Size_limits)

Apparently the common block size for ext3 partitions is 4kB, which gives a maximum file size of 2TB, and a maximum filesystem size of 16TB.

---

### Post by fjgaude on 2008-05-14
Yea, you are so right... if one is into the fastest type file server setups I would think one would look into JFS and XFS or wait for ext4, these having de-fragmentation and extents capabilites.

---

### Post by psusi on 2008-05-15
> 2TB filesystems are supported just fine in Linux with ext3.  For that matter, windows can do it too.

Why raid6 instead of raid5?  Do you really need to be able to tolerate TWO disk failures in a home server?

Fragmentation isn't really worth worrying about but if you really want to defrag an ext3 filesystem, you can always install the defrag package, though you will need to do this on the livecd to defrag your root filesystem since it needs to be unmounted.

---

### Post by talz13 on 2008-05-15
> **psusi said:**
> > 2TB filesystems are supported just fine in Linux with ext3.  For that matter, windows can do it too.

Why raid6 instead of raid5?  Do you really need to be able to tolerate TWO disk failures in a home server?

Fragmentation isn't really worth worrying about but if you really want to defrag an ext3 filesystem, you can always install the defrag package, though you will need to do this on the livecd to defrag your root filesystem since it needs to be unmounted.

Well, if I had 6TB of data, I'd appreciate the added redundancy ;)

---

### Post by brianmac64 on 2008-05-15
> **talz13 said:**
> Well, if I had 6TB of data, I'd appreciate the added redundancy ;)

Dude, I think that would be only ~4TB of usable space in RAID-6, or ~5TB in RAID-5.

---

### Post by talz13 on 2008-05-16
> **brianmac64 said:**
> Dude, I think that would be only ~4TB of usable space in RAID-6, or ~5TB in RAID-5.

Still, that's a lot of data to backup via USB or DVD (even blu-ray if you go that route).

---

### Post by |{urse on 2008-05-16
you need to install gpt (gnu partition table) to surpass the > 2tb (yes, ext3 has a > 2tb limit) Please note, gpt is not bootable. also be sure to familiarize yourself with tw_cli as the http app does goofy things on linux with really large volumes.

---

### Post by |{urse on 2008-05-16
> **talz13 said:**
> Still, that's a lot of data to backup via USB or DVD (even blu-ray if you go that route).

also remember that he isnt going to be fitting 6 full tb onto a disc, just whatever blocks are written + compression (i prefer gzip, because bz2 is horrendously slow for a slight improvement in compression). So you could use partimage and multiple dvd's or blu-rays preferably a very large external hdd or nas.

google sysreccd, it uses partimage for backing up/cloning/restoring large volumes.

---

### Post by |{urse on 2008-05-16
to install gpt you need to install parted (i think its already installed though)


sudo parted /dev/sdb
mklabel gpt
quit


again, this volume will no longer be bootable so the smart thing would be to have your os on a seperate volume.

---

