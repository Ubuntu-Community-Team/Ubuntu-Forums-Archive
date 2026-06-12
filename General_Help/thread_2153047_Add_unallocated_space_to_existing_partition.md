---
title: "Add unallocated space to existing partition?"
date: 2013-06-09
forum: General Help
---

### Post by gigenieks on 2013-06-09
Hello!

[[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Partitioning/th_Disks_002_zps96dfdf70.png[/IMG]](http://s59.photobucket.com/user/gigenieks/media/Partitioning/Disks_002_zps96dfdf70.png.html)
(Click on screenshot to see larger picture)

Basically I want to add unallocated space of 26 GB's to existing 66 GB NTFS partition.
Tried a few searches didn't found relevant information for this particular case...

Any guidance? Links?
I would appreciate.

P.S. _Later_, I'm probably will want to change that partition from NTFS to ext4.

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by CharlesA on 2013-06-10
Bad sectors are just a sign of age. I would monitor the disk and make sure the number of bad sectors does not increase dramatically.

I've got a disk with 18 bad sectors, but so far that number hasn't increased, so I'm fit to leave it, cuz I have everything backed up if and when that disk dies.

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by CharlesA on 2013-06-10
Daily/Monthly backups, but the point is if the number of bad sectors isn't increasing you should be "OK."

It probably helps that I have my storage array do a verify every two weeks, and that is what has caught the bad sectors - not random file access.

---

### Post by gigenieks on 2013-06-10
Really helpful answer, ahallubuntu. I managed to successful resize with Gparted.

> **ahallubuntu said:**
> 
a) Those 28 bad sectors are worrisome.  I'd install GSmartControl and see exactly that those are (Attributes tab) - Reallocated Sectors or Pending Sectors?
b) I'd also run an extended S.M.A.R.T. test with GSmartControl.

[[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Partitioning/th_GSmartControl_Attributestab_zpsfbfa992a.png[/IMG]](http://s59.photobucket.com/user/gigenieks/media/Partitioning/GSmartControl_Attributestab_zpsfbfa992a.png.html)
a) They are Reallocated Sectors as seen in screenshot.

b) Run Extended test which didn't found any errors.

---

