---
title: "Disable boot screen?"
date: 2006-10-24
forum: General Help
---

### Post by johann_p on 2006-10-24
Is there a way to completely remove the boot screen and instead show the boot log messages?

---

### Post by ~LoKe on 2006-10-24
You should simply remove "quiet" from the kernel line in /boot/grub/menu.lst to see the text.  Remove "splash" to get rid of usplash as well.

---

