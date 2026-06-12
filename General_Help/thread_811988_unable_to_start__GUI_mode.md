---
title: "unable to start  GUI mode"
date: 2008-05-29
forum: General Help
---

### Post by babyrajT on 2008-05-29
How to reset the xorg file to default configuration in ubuntu 7?

The Gui mode hangs when booting .It is showing running local scripts.........

Thanks

---

### Post by lswest on 2008-05-29
either boot into recovery mode (or if you can get to a terminal login on normal boot do it that way) login and then type ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` it should get you at least a working GUI.

---

### Post by babyrajT on 2008-05-29
Hi,

While booting it is showing "running local scripts" and hanging.
But can login to tty123346

Thanks

---

### Post by babyrajT on 2008-05-29
ran that command and could login to gui but unable to change resolution from 800x600

Thanks

---

### Post by john91 on 2008-05-29
you probably need to switch to a different video driver.  check restricted drivers (system>administration>restricted drivers) and see if there's a video driver there.  if so, enable it and restart X.  if that doesn't work, we'll need more info to debug your system.

---

### Post by babyrajT on 2008-05-29
Thanks that helped.

---

