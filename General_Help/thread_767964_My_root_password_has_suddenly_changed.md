---
title: "My root password has suddenly changed"
date: 2008-04-26
forum: General Help
---

### Post by chris.olsen on 2008-04-26
I am tweaking things here and there, then all of a sudden I try to install some libraries and my root password is no longer working.  I used it a dozen times just before.

What happened?

---

### Post by tamoneya on 2008-04-26
no clue what happened there.  easy way to fix it is to boot into recovery mode.  Hit esc when GRUB loads and select recovery mode.  This will boot you into commandline with root privileges.  Then execute```
passwd root
```

---

### Post by conscious on 2008-04-26
Wait, you're not supposed to have a root password at all. Is it sudo that's not working? What exactly is wrong?

---

### Post by chris.olsen on 2008-04-26
turned out it was a periodically bad key on the keyboard that was the issue.

Thanks for the help.

---

