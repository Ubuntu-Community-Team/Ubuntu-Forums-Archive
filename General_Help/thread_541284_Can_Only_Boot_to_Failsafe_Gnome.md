---
title: "Can Only Boot to Failsafe Gnome"
date: 2007-09-02
forum: General Help
---

### Post by taekwondodogoof on 2007-09-02
Hi,

I recently installed Gutsy, and was trying to get Compiz to work. When I restarted at one point, right after I logged in, I would get stuck at the tan screen with only my cursor. I can boot normally into gnome using failsafe gnome, but I would like to fix this and have my services start. I've tried turning off all the services and booting again, but that didn't work.

Thanks for your help!

---

### Post by tzulberti on 2007-09-02
Try doing the following: "mv .gnome .gnome-backup" from a console, as the normal user. Then try to login into gnome. It should appear at the default configuration.

---

### Post by Endolith on 2007-12-14
If you rename ~/.gnome2/session, it will load the default session, as far as I can tell.

---

