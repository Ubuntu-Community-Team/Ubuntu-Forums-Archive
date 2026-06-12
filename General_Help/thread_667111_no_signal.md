---
title: "no signal"
date: 2008-01-14
forum: General Help
---

### Post by pedrom169 on 2008-01-14
I re-installed ubuntu and it started up fine. The orange bar went across like normal.
but it got the loading the log on screen. the monitor lost signal.
but i can still press ctrl + alt + F1 to get to the black screened terminal.

any help?

Cheers

Peter

---

### Post by Craigus on 2008-01-14
From text terminal, do:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

---

### Post by pedrom169 on 2008-01-14
thanks :)
it works now

---

