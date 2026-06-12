---
title: "Logical/Primary Partition Problems"
date: 2006-07-15
forum: General Help
---

### Post by Lunar_Lamp on 2006-07-15
I had 4 primary partitions:

1 Windows
2 Swap
3 Ubuntu /
4 /home

I shrank the windows partition by 20gb, to give a bit more space to my Ubuntu installation, the intention being to mount it at /home/usr/media.

The problem of course is that I can only have 4 primary partitions.

So I deleted the swap partition, and created an extended partition that held the new 20gb partition and a swap partition.  When I tried to boot into linux I got a kernel panic, though windows would boot perfectly.

Currently I have managed to resolve the situation to a degree where I have the same partition layout as before, but with the windows partition shrunk and 20gb of unallocated space.  How do I go about getting this to be what I want it to be - another partition (ext3) that I can use?

---

### Post by Denis on 2006-07-15
You did change the location of the swap partition in fstab, when you created this new layout?

This line has to be changed to the new device in /etc/fstab
```
/dev/hda6       none            swap    sw                         0       0
```
You can change this file from a live CD.

---

### Post by Lunar_Lamp on 2006-07-15
I did. :(

I also rebooted the live CD to check that the changes had properly updated.  I just changed the current swap line from /dev/hda2 to /dev/hda6 (or whatever the correct numbers were).

---

