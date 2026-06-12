---
title: "GParted and QtParted show different partition info"
date: 2007-04-20
forum: General Help
---

### Post by RavanH on 2007-04-20
Has anyone noticed this?

I have 8 different partitions on one disk, to accomodate a Win XP / Ubuntu Feisty dual-boot (each 3 partitions) with an extra FAT32 partition for exchanging files between the two and one hidden factory restore partition...

Bit complicated I know ;) but when I tried to resolve a problem with swapping in Ubuntu Feisty, I noticed that QtParted and GParted showed a difference in disk partition info:

My linux-swap partition in GParted was /dev/hda7 but in QtParted it was shown as /dev/hda8... I believe that GParted shows the correct info, as the last partition I have created (by resizing another partition with GParted LiveCD some time ago) was not the linux-swap partition.

Would this make QTparted unreliable? Or is GParted mistaken?

Version info:
GParted 0.2.5
QtParted 0.4.5-cvs
Qt 3.3.7
on
Ubuntu Feisty Fawn (beta) kernel update .20-15

---

### Post by pjman on 2007-04-20
I don't know if I can help but can you post screenshots?

---

