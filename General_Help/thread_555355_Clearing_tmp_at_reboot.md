---
title: "Clearing /tmp at reboot"
date: 2007-09-20
forum: General Help
---

### Post by oznelig on 2007-09-20
Today I just lost quite a bit of fortunately not too hard to replicate work
because I didn't realize that Ubuntu Gutsy Tribe 5 seems to clear /tmp
at logout/reboot.
I previously used Suse and it never did that.
Any suggestions on how to stop it from doing that ?

Thanks,

Enzo

---

### Post by dcstar on 2007-09-20
> **oznelig said:**
> Today I just lost quite a bit of fortunately not too hard to replicate work
because I didn't realize that Ubuntu Gutsy Tribe 5 seems to clear /tmp
at logout/reboot.
I previously used Suse and it never did that.
Any suggestions on how to stop it from doing that ?

Thanks,

Enzo

Edit /etc/default/rcS and change the TMPTIME setting and it will keep "X" days of files instead.

---

### Post by oznelig on 2007-09-20
It worked, thanks!

Enzo

---

