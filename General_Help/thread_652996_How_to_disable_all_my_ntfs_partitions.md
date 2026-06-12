---
title: "How to disable all my ntfs partitions"
date: 2007-12-29
forum: General Help
---

### Post by Mr.Johnny on 2007-12-29
Hi... 

I did the etc/fstab commenting, but the partitions still show up for mounting when I open "Computer".

Didn't find any conclusive response in the other similar threads for disabling ntfs support.

thanks

---

### Post by smbm on 2007-12-29
You could try removing the ntfs3g packages and blacklisting the ntfs kernel module.

---

### Post by Mr.Johnny on 2007-12-29
Unfortunaly, if I try to unninstall any of those, it also says I must unninstall ubuntu-desktop (I guess I don't want that)...

Hum... blacklist the module? how do I do that?

thanks

---

### Post by harold4 on 2007-12-29
Post your /etc/fstab to verify they are commented out correctly.

---

### Post by Mr.Johnny on 2007-12-29
I'll post it tomorrow, I'm don't have access to that computer now. 

I think they are, because none of the ntfs partitions are mounted on startup now, but they still show up when I click on the "Computer" icon (right click on any of those shows the "mount" option).

I don't want them to be shown too (if that's possible).

---

