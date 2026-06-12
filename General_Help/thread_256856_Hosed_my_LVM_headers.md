---
title: "Hosed my LVM headers"
date: 2006-09-13
forum: General Help
---

### Post by AusIV4 on 2006-09-13
When I set up my Ubuntu Box, I had the following drives:

/dev/hda: 250 GB - LVM

/dev/hdc: 120 GB:
     hdc1: Boot partition
     hdc2: Swap
     hdc3: LVM (with 250 GB volume)

/dev/hdd: 40GB - Unused

I used the LVM volume as my home directory.

Recently I purchased a new disk and wanted to pursue a RAID setup, but that isn't the point here. 

I was trying to move my boot partition to /dev/hdd1, but instead of typing:
```
dd if=/dev/hdc1 of=/dev/hdd1
```
I typed
```
dd if=/dev/hdc1 of=/dev/hda1
```
I almost immediately realized my mistake and stoped the transfer, but LVM no longer recognizes /dev/hda1.

Now since that time, I've found problems with the general syntax of the statement I was trying to make, and I really don't need critiqued on that.

What I need to know is whether or not there is any way to reconstruct my LVM headers so that I can mount my volume and hopefully recover some important data. The other volume in the LVG, /dev/hdc3, should be completely intact if that helps.

Any help is greatly appreciated.

---

### Post by The Soundophiliac on 2006-09-18
I messed up with dd once, too. I didn't find any way to recover data, however, my situation was different if I remember correctly. You might have more luck.

---

