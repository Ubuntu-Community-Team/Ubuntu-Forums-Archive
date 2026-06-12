---
title: "[SOLVED] access my install from live CD"
date: 2008-01-16
forum: General Help
---

### Post by skymera on 2008-01-16
hi 

im in the live CD currently and wish to add/remove packages from my installed ubuntu.

how would i go about doing this?

so when i "sudo apt-get remove <blah>" it will do it on my install?

i have mounted my install on /media/ubu

---

### Post by geirha on 2008-01-16
You could try this in a terminal ```
sudo chroot /media/ubu
aptitude install something
aptitude remove something
```

Any reason why you can't do this by booting the installed system itself?

---

