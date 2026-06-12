---
title: "theme wont go away [Resolved]"
date: 2007-01-13
forum: General Help
---

### Post by heathen on 2007-01-13
yeah, I installed a gtk2 theme and now it wont go a way...  I can't get clear looks back.. it's black and orange all of a sudden..  my taskbars are not right either...

running edgy...  I've restarted X and the computer...  not sure where to start now...

---

### Post by heathen on 2007-01-14
anyone?

---

### Post by Theimon on 2007-01-14
Can you delete it from /usr/share/themes ?

---

### Post by heathen on 2007-01-14
no, the theme isnt there.  i downloaded from gnome-look and installed myself..

---

### Post by ardchoille42 on 2007-01-14
If you downloaded and installed it as normal user, the theme will be in ~/.themes. You can move it to another directory or delete and it should go away.

User themes (themes installed as normal user) - /home/USERNAME/.themes
System-wide themes (themes installed as root) - /usr/share/themes

User icons (icons installed as normal user) - /home/USERNAME/.icons
System-wide icons (icons installed as root) - /usr/share/icons

---

### Post by heathen on 2007-01-14
thanks... that fixed it..

---

