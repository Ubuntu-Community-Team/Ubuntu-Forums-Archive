---
title: "Transferring software array to new machine"
date: 2015-11-26
forum: General Help
---

### Post by Headcase_Fargone on 2015-11-26
Hi all,

A few years ago I built a small media server running Ubuntu off an SSD with a software RAID5 consisting of four HDDs.  The motherboard is starting to have some issues and needs to be replaced.  The trouble is I'm concerned about losing data on my array if I do so.

I'm a Linux novice, and it took me a good long while to get this set up properly.  Is it possible to set up a new motherboard with a fresh installation of a newer version of Ubuntu and still rebuild this array without data loss?  Unfortunately since it's my media server I don't have the space to make backups anywhere else.

It's been years but I *believe* I used mdadm to set this up.

---

### Post by TheFu on 2015-11-26
Backups are not optional.

However, I've moved SW-RAID arrays across multiple systems without issue. Just need to put the device into the new fstab.

If the data is important enough that HA (i.e. RAID) is needed, then certainly it is important enough to have versioned backups which solve 999x more problems than RAID-anything can.

RAID is not a backup.

---

