---
title: "ZFS Help!"
date: 2013-08-20
forum: General Help
---

### Post by michael28 on 2013-08-20
After installing Ubuntu 13.04 on a USB Flash Drive for a NAS box, I decided that it was waaaay too slow (constant freezes and hangs).

So, rather than hunting for a better class of USB drive, I opted to buy a Raid controller and run Ubuntu off of two 500gb Raid-1 configured drives.

I used the Live CD to clone my USB Drive over to one of the 500gb drives, then used raid controller to copy existing data to second drive, and everything worked perfectly.

Here is my problem:

Before setting up the Raid controller, I created a ZFS mount for my media on 6x2TB HDDs.

The HDDs were as follows:

1-sda
2-sdb
3-sdc
4-sdd
5-sde
6-sdf

The problem is that after installing the raid controller and plugging in the two 500gb drives, they were assigned

7-sda
8-sdb

Meaning, that my ZFS that had the old sda and sdb "letters" is now "corrupt" (not really, when I plug in old usb flash drive, works fine).

My question is, how do I either recreate zfs pool without losing data and having it populate sda to sdg and sdb to sdh on ZFS pool. Or, do I have to work through UUID to assign new drive letters to the 2x500gb OS drives?

Phew. Thank you.

---

### Post by michael28 on 2013-08-20
My research has taught me that maybe the best solution is to use UUID on my 2x500gb OS drives that are in a Raid array? But I get issues (probably because its in a raid array) about super-blocking when trying to rename UUID.

---

