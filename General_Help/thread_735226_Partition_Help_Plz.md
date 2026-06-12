---
title: "Partition Help Plz"
date: 2008-03-25
forum: General Help
---

### Post by broken sword on 2008-03-25
Hello all

I just purchasd a new laptop, Dell XPS 1530.  It's set to dual boot Vista Ultimate and Ubuntu.  The partitions are as follows:

102 MB partition (i'm assuming that this is boot info)
10 GB Recovery ( Dell Recovery)
30 GB Vista Partition
486 MB Swap Partition
20 GB Ubuntu Partition
120 GB Data (shared data between Ubuntu and Vista)
2.5 GB unknown partition

XPS specs: 2.5 core 2 duo processor, 4 GB RAM, 200 GB HD

I made my Vista partition too small, only have 10 GB for apps, I would like to resize this to add at least 10-15 more GB (will be installing some games, photoshop, acrobat).  But I can't resize the partition using Gparted, or Vista extend volume command, any suggestions?

Should I try to use a third party program, will it work? 
Will it damage my installs?
How should I resize the partition? In Ubuntu? in Vista? CD?

if you need anymore info, please let me know.  Any assistance will be greatly appreciated.

---

### Post by pointone on 2008-03-25
You'll need to shrink the data partition (or some other partition) before growing the Vista partition. Presumably, if your partitions are ordered in the way you described here, you'll need to shrink the data partition, then shift the Ubuntu and swap partitions to the right before growing the Vista partition. In short, GParted should work fine. Is it giving you a specific error message? Keep in mind you'll have to unmount any partitions you're working on. Running GParted from the Ubuntu live CD is usually the best idea.

On a side note, LMFAO @ Vista taking up 20 GB out of the box. :P

---

### Post by broken sword on 2008-03-25
I can't extend the Vista partition at all, I've tried GParted, and I've tried Partition Manager.  I was going to try to convert the disk to a dynamic disk (hoping that I can extend the Vista partition), will Ubuntu work on a dynamic disk?  If not, I'll just have to restore the factory settings and partition it right this time.

---

