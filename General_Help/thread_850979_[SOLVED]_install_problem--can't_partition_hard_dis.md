---
title: "[SOLVED] install problem--can't partition hard disk"
date: 2008-07-06
forum: General Help
---

### Post by benner on 2008-07-06
the hard disk is 60 gigs. it shows 42 gigs free.  but the installer won't let me resize. gparted won't let me resize either. i am trying to set up a dual boot. there is already a copy of xp on it. any suggestions?  thanks in advance...

---

### Post by lisati on 2008-07-06
First thought: defrag the Windows partition two or three times before trying to modify the partision.
Second thought: Is the "free space" still part of the Windows partition that you are trying to resize?

---

### Post by benner on 2008-07-06
already defragged. trash bin is empty. sda1 is the only partition and it takes up the whole disk-60 gigs.

---

### Post by hal8000 on 2008-07-06
If gparted wont resize it you can either try ntfsresize or a windows utility e.g. acronis.

From the live cd environment install ntfsprogs

sudo apt-get install ntfsprogs

According to what you say you should see a single partition so at a terminal
sudo fdisk -l

should list a single partiition containing all your hard drives cylinders.
then try ntfsresize

e.g.

sudo ntfsresize -40G /dev/sda1

will shrink your first partition to 40G, HOWEVER, make sure you backup all your personal data on your windows partituion first, music, bookmarks, any files you want to keep etc

---

### Post by benner on 2008-07-07
worked great. thanks so much.

---

