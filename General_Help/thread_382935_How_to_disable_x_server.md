---
title: "How to disable x server"
date: 2007-03-12
forum: General Help
---

### Post by Utael on 2007-03-12
Can some one help me figure out how to disable the x server im having troubles installing drivers and it keeps telling me to disable x server

---

### Post by kpkeerthi on 2007-03-12
press cntrl + alt + F1 and try installing your drivers

---

### Post by Utael on 2007-03-12
thank you

---

### Post by Utael on 2007-03-12
That didnt work

---

### Post by denver on 2007-03-12
> Control+Alt+F1  ( to enter a virtual terminal )

> sudo /etc/init.d/gdm stop  ( to stop the Xserver )

After you finish what you want to do, simply type:

> sudo /etc/init.d/gdm start

---

