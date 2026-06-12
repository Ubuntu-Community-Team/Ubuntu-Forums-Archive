---
title: "Ubuntu 18.04 Desktop Keeps Crashing"
date: 2018-09-22
forum: General Help
---

### Post by chrscrlsn on 2018-09-22
Hello,


I'm running Ubuntu 18.04 on a Lenovo Ideapad 320 with 8GB of RAM and an AMD Radeon R7 series graphics card. Periodically, the screen will go black for a split second before returning me to the login screen. When I log back in, whatever applications I had open will be closed and any work will be lost. Anybody have any idea why this keeps happening and what I might do to stop it?


Thanks!

---

### Post by jeevanthanal on 2018-09-24
Maybe graphics driver issue

---

### Post by HermanAB on 2018-09-24
Try a different (simpler) desktop system and see if it persists:
$ sudo apt install xfce4

If it works, then the problem is with Gnome.

If it also fails, then the issue could be hardware or device driver related.

---

