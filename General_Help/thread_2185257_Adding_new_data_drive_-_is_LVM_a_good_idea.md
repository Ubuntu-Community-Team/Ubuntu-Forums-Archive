---
title: "Adding new data drive - is LVM a good idea?"
date: 2013-11-01
forum: General Help
---

### Post by spookybathtub on 2013-11-01
I'm running an HTPC on Ubuntu 12.04.  The system is on a small SSD, and I have a 1TB internal drive for movies, etc.  That drive is almost full, so I plan to add a second internal 1TB drive, but am unsure of the best way to do so.  Since I've spent a long time getting all my apps configured already, it would be convenient to add the disk to the same volume as my existing disk.

I don't want RAID 0, because of the doubled risk and I don't need the speed.  It seems like LVM can create a single volume spanning both disks.  If I do that, and one disk fails, is it easy to recover the data from the good disk?

Since I am not currently using LVM, how can I convert my existing disk to it and add the second one without losing data?

Is there a better option than LVM?

---

### Post by bab1 on 2013-11-01
> **spookybathtub said:**
> I'm running an HTPC on Ubuntu 12.04.  The system is on a small SSD, and I have a 1TB internal drive for movies, etc.  That drive is almost full, so I plan to add a second internal 1TB drive, but am unsure of the best way to do so.  Since I've spent a long time getting all my apps configured already, it would be convenient to add the disk to the same volume as my existing disk.

I don't want RAID 0, because of the doubled risk and I don't need the speed.  It seems like LVM can create a single volume spanning both disks.  If I do that, and one disk fails, is it easy to recover the data from the good disk?

Since I am not currently using LVM, how can I convert my existing disk to it and add the second one without losing data?
Before you do anything else you should backup all of your data!  

I always create the LV on bare disks and move the data onto the LV.  This howto explains it well: [http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/]("http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/")

There are however, 2 scripted ways to create LVM on disks with data (after you backup your data!!!) see [blocks]("https://github.com/g2p/blocks#readme") and [mhddfs]("https://romanrm.net/mhddfs").  I  have never used either of these scripts.

In the Ubuntu wiki is this:[ SettingUpLVM-WithoutACleanInstall]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall")> 

Is there a better option than LVM?
There is only LVM or Oracle (SUN) ZFS pools.  LVM native to Linux and I prefer it. You might try finding @rubylaser on this forum.  He works with all of this and might have an opinion one way or the other.

---

