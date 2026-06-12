---
title: "re: gparted wont do work"
date: 2008-02-29
forum: General Help
---

### Post by fallsoff on 2008-02-29
Hello,
I have a dual boot Ubuntu/ xp laptop. I need to adjust the Ubuntu partition sizes and gparted just sits there and displays the partition information, but will not allow me to initiate any changes. The controls are greyed out.

I am root. How do I get this to happen? I a trying to squeeze Suse 10.3, Gutsy and XP on a 30 gig drive. Partition Magic will not show the main Linux partition only the swap space so I have to use gparted.

Any input? 
Thanks in advance,
fallsoff

---

### Post by kesman on 2008-02-29
You cannot edit the root directory since the partition is mounted and active. Download the gparted LIVEcd and boot from it to edit the partitions. This may cause some troubles so I'd suggest you to backup first.

---

### Post by bodhi.zazen on 2008-02-29
You can use the Ubuntu Desktop CD to do it as well.

You may need to unmount your swap partition

---

### Post by fallsoff on 2008-03-01
Kesman and Bodhi__thank you.
 I will get the gparted disk for my utility stash, I had tried with the live CD but couldn't seem to get any traction. I assumed the live disk wouldnt do any real work on the metal. I will try that again. I had not attempted to unmount the disk before and I will do that first,'Thank you both for the response.
fallsoff

---

