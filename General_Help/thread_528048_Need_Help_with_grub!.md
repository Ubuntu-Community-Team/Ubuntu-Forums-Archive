---
title: "Need Help with grub!"
date: 2007-08-17
forum: General Help
---

### Post by austin8159 on 2007-08-17
I love ubuntu, but I need to remove it (I won't explain WHY) but I want to put Windows XP in it's place.
I have Windows Vista on one partition and all the necessary linux parts on other partitions as well, and i want to be able remove Ubuntu, and then Install XP where Ubuntu was...
I'm not explaining this well :( ...
I want to keep grub, but get rid of Ubuntu, and put XP as a choice on Grub...
(I have the XP disc and everything)

SO
Basically, i want to remove Ubuntu and make it so that when I turn my computer on, grub asks me whether i will boot Vista Or XP...

---

### Post by cmillican on 2007-08-17
You'll need to delete your Ubuntu partitions, install Windows on them, then use a live CD like Super Grub Disk or just an Ubuntu CD (my preference, for internet support availability) to reinstall GRUB. There are several HOWTO's for this on these forums.

---

### Post by austin8159 on 2007-08-17
Will deleting the linux partitions remove grub?

---

### Post by jns-nun on 2007-08-17
Look, everydoby knows what in all instalations you can manage de partition to use or the group of partitions. In w*ndows you need set the partition(s) in the begin of instalation setting up the table how you want.

Note: I can give a better explanation in spanish.

---

### Post by mikewhatever on 2007-08-17
> Will deleting the linux partitions remove grub?
No it will not, at least not from the MBR, but XP will overwrite the MBR with its own boot loader.

---

