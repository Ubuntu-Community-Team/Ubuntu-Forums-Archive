---
title: "Beryl in start-up restarts X"
date: 2007-06-10
forum: General Help
---

### Post by ZERO_SHIFT on 2007-06-10
I started playing with my laptop, however now when I leave Beryl in the starup program scripts it restarts my X server as I begin a new session.

Is there a way of keeping Beryl on the startup programs script without X restarting as it starts?

If not I might have to re-INSTALL ubuntu, in that case is there a way of saving my firefox bookmarks? and Evolution mails?

Thanks in advance

Long Live the Community

---

### Post by LollYouSuckZor on 2007-06-10
Boot in terminal, 
```

sudo apt-get remove beryl beryl-core beryl-plugins

```
Reboot.  You probably installed beryl incorrectly.  Use synaptic? How did you install it in the first place?

---

### Post by ZERO_SHIFT on 2007-06-10
Thanks a lot

I did completely remove and then install and everything fine now.

:popcorn:

---

### Post by LollYouSuckZor on 2007-06-10
Haha! Yay! I helped my first person :D!!

---

### Post by LollYouSuckZor on 2007-06-11
One more thing, go into the snypatic or adept manager and remove the rest of Beryls stuff before you install it again, remember that code, it comes in handy :D

---

