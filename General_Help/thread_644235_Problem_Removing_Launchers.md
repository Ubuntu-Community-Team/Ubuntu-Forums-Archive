---
title: "Problem Removing Launchers"
date: 2007-12-18
forum: General Help
---

### Post by Vazguard on 2007-12-18
Hey all:

I just finished setting up Photoshop CS2 on my Ubuntu boot.  I have two launchers on my desktop that I'd like to remove, both for my copy of Photoshop 6.0.  They link to the PS6 folder on my windows hard drive; created them through the 'make link' option.  But when I go to delete them I get this error:

Error "Not on the same file system" while deleting "/home/NAME...otoshop 6".
Would you like to continue?

and two buttons, one Retry and one Cancel.  Pressing retry merely brings up the same error box.

Is there a way to delete them?

Thanks,

Vaz

---

### Post by forestpixie on 2007-12-18
try shift+delete

think that's what I did in that position - or I might have needed to open nautilus as root

```
gksudo nautilus
```

---

### Post by Vazguard on 2007-12-18
Thanks, the Shift-Del combination worked.

---

