---
title: "Swap File not used"
date: 2007-10-18
forum: General Help
---

### Post by Niniel on 2007-10-18
Hello,

I shrunk my swap file, but now it looks like it's not being used anymore. First off, I have to manually switch it on, but even then it doesn't look like it's being used.
How can I fix that?

---

### Post by rbmorse on 2007-10-18
open a terminal and enter

blkid

Find the line with "type=swap" and note the UUID string for that partition.

Then, also in a terminal, 

gksu gedit /etc/fstab

Again, find the line that corresponds to the swap partition and compare the UUID= string here to that posted in blkid.  If they are different, change the string in the fstab file to match the value shown by blkid. 

Save, close gedit and then in a terminal 

sudo mount -a

To verify the swap file is now working, do system > administration > system monitor. Click on the "resources" tab and check the "memory and swap" display to ensure the presentation is sane.

---

### Post by Niniel on 2007-10-19
Ok, that worked, the swap partition is now being automounted and reported to be in use. However, the "used" and "unused" columns still only show "---". Any idea why?

---

### Post by crosswalker21 on 2008-03-04
I had the same thing happen to me.  The fstab trick fixed it as well.

---

