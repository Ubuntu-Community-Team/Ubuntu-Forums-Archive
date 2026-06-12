---
title: "Renaming Mounted Partitons"
date: 2006-12-18
forum: General Help
---

### Post by indytim on 2006-12-18
I want to rename some of my mounted partitions in Kubuntu 6.10 to something more informative.  In the past with Ubuntu 6.06 I did the following

1.  create a directory in /media with the appropriate name.
2.  set the ownership and group to my loginid
3.  edit fstab and duplicate the line entry of the subject mountpoint, changing the name from say "sdb3" to "LxMedia".
4.  re-boot.

I just went in to do the same in K6.10 and all went well until I came to the fstab.  I noticed that each fstab entry has a uuid=<long string>.

My guess at this point is that the uuid is a system-generated alpha-numberic and by duplicating it in the fstab, bad things will happen.

Any easy alternatives to the steps described above for Kubuntu 6.10?

Tx,

IndyTim

---

### Post by po0f on 2006-12-18
indytim,

I've had no problems using the old way (ie, /dev/hda6 instead of UUID) for partitions that I created myself, and I'm sure it would work for the partitions that (K)Ubuntu created as well.

---

### Post by indytim on 2006-12-18
Thanks,

I'll give it a try.

IndyTim

---

