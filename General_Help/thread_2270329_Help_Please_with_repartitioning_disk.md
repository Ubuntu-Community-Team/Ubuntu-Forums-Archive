---
title: "Help Please with repartitioning disk"
date: 2015-03-22
forum: General Help
---

### Post by bobnutfield on 2015-03-22
Hello Everyone

I can't believe how much I have forgotten.  4 or 5 years ago I wouldn't have needed to ask these questions but I just can't remember now.

My disk on my old laptop is 160GB.  I have three distributions installed, and the disk is partitioned as follows:

SDA1           EXT4          11.72GB       UBUNTU SYSTEM FILES
SDA2           EXT4          29.29GB       HOME
SDA3            LINUX SWAP
SDA4           EXTENDED
SDA5           EXT4          11.18          FEDORA SYSTEM FILES
SDA6           EXT4          27.94          FEDORA HOME
SDA7           EXT3          11.18          SLACKWARE SYSTEM FILES
SDA8           EXT3          55.59          SLACKWARE HOME


All I want to do is delete Fedora and Slackware parttions and extend the Ubuntu system files to 15 or 20 GB, keep the swap partition as is, and the rest for Ubuntu home.  My questions are:

1.  Do I just delete the unwanted partitions and format as EXT4 and then resize the Ubuntu home partition?

2.  I assume the boot files are on SDA1.  If I do this operation, will I screw up the booting of the computer?

I have years of important work on  this computer and I really like it.  If some kind soul who is an expert at repartioning would help, I would greatly appreciated it.

Bob

---

### Post by bobnutfield on 2015-03-22
Never mind....figured it out

---

### Post by Bucky Ball on 2015-03-22
Good news. Please mark the thread as solved. See second link in my signature for how.

---

