---
title: "[SOLVED] parted: accidentally deleted my home partition"
date: 2007-10-30
forum: General Help
---

### Post by abrichr on 2007-10-30
I made a really boneheaded move, and whilst attempting to create a new label on hdb, I made parted create the new label on sdb, which contains sdb1, my /home partition.

sudo fdisk -l shows no partitions on that drive.  but so far, everything seems to be fine; i'm able to edit files in my home directory, and my downloads are still downloading.

i'm pretty sure once i restart the computer i won't be as lucky.  any suggestions?

---

### Post by dabl on 2007-10-30
I don't think the mere act of adding a label to an existing partition will affect anything, except perhaps how it shows in Nautilus or something like that.

Moreover, if it you don't want it labeled, just run GParted and delete the label.  :)

---

### Post by abrichr on 2007-10-30
Well, I restarted, and everything's ok.  I forgot that my downloads/home directory were actually on another partition.  This one had nothing important on it :)

---

### Post by dabl on 2007-10-30
Oooooooooooooooohhhhh -- that is one VERY empty hard drive!  8-[

---

