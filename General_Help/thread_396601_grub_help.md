---
title: "grub help"
date: 2007-03-29
forum: General Help
---

### Post by RanShak on 2007-03-29
My situation: I'm dual booting XP and Ubuntu Edgy on separate drives and need to remove Ubuntu for the time being. I've tried once already, but didn't realize that removing Edgy would remove GRUB, leaving my computer functionless. I've read a lot of how-to's, but all seem to require a floppy drive. Any help?

---

### Post by divague on 2007-03-29
boot from the windows xp cd and at some point it will give 3 choices one of them is a recovery console (or something like that), go there and when it finishes loading put:

fixmbr

this should remove grub

---

### Post by RanShak on 2007-03-29
I don't actually have an XP CD. I'm using an emachine with 4 recovery disks and the 1st disk loads PC Angel.

---

