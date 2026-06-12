---
title: "Resizing my Ext3 Partition"
date: 2006-07-09
forum: General Help
---

### Post by krazykirk on 2006-07-09
Hi Everyone,

I want to allocate more space to my Ext3 linux partition, so my plan is to resize my 130gb NTFS partiton and give the extra space to my Ext3 partition.

I plan to use Gparted.

My Question is, would it would be safe? As in would ubuntu still work even if the partition size changes?

---

### Post by krazykirk on 2006-07-09
hmm.. it looks like you can't resize NTFS in gparted!

So i think i'll boot into Windows and try it with partition magic...

I'll tell you how it goes...

---

### Post by mgor on 2006-07-09
not sure how it is these days. but a couple of years ago it wasen't safe. if you want to be able to resize paritions, even having them span over more then one harddrive, LVM is the way to go.

---

### Post by Rui Pais on 2006-07-09
> **krazykirk said:**
> Hi Everyone,

I want to allocate more space to my Ext3 linux partition, so my plan is to resize my 130gb NTFS partiton and give the extra space to my Ext3 partition.

I plan to use Gparted.

My Question is, would it would be safe? As in would ubuntu still work even if the partition size changes?

Hi,
what you pretend to do is sometimes more difficult then appears at first.

If NTFS is the first partition and Linux on the second, gparted may not move the Linux partition to the free space alocated by Windows shrink. 
A worst scenario is when the partitions are logical ones inside a big extended partition. You'll then need to resize the extended and move the logical partitions, falling in the previous case.

The best options is, try to free at least as many free space as the linux partition you want to move/resize. In same cases that allow to move it or at least duplicated there, delete the old, and resize the new one on the new position to the space ocuppied to the old one (sounds difficult but its easy indeed).

And i thing is better and safer no resize NTFS partitions with Windows tools. You have partion Magic. Go with it for NTFS resize.

About safety. Nothing is safe. Playng with partitions is a deleicate thing. Make backups of all important personal data. 
Usaully there is no problems. (The problems starts when things don't go so well ;))

---

### Post by bigken on 2006-07-09
this how I have done on nemerous times using the sysrccd download
the iso 1st [http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page) burn to disc you must defrag
win xp 1st this a must then boot from the rescue CD  run_qtparted and resize your partions it may seem to hang dont worry just be pacient ;) hope u find this helpful

---

### Post by krazykirk on 2006-07-09
Well I just used partition magic (booted into windows) and it all worked out fine! Thanks for all the help anyway! :)

---

