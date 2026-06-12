---
title: "logout window????"
date: 2006-09-08
forum: General Help
---

### Post by vincentvee on 2006-09-08
anyone know how i might be able to change the logout window on my kids user accounts so there is only log off, switch user, and reboot buttons??
they have problems with which button to hit......

vincent

---

### Post by Rui Pais on 2006-09-08
> **vincentvee said:**
> anyone know how i might be able to change the logout window on my kids user accounts so there is only log off, switch user, and reboot buttons??
they have problems with which button to hit......

vincent

Do you mean, remove the Hibernate and Suspend buttons?
If so, in your kids account run from a terminal gconf-editor or in Main Menu look for Applications->System Tools->Configuration Editor.  

Navigate to:
/apps/gnome-power-manager
You have there 2 keys, can_hibernate and can_suspend both with checked marks. To remove the buttons uncheck them.

---

### Post by vincentvee on 2006-09-08
thanks bud....that done the trick

---

### Post by Rui Pais on 2006-09-08
No problem
(i have done the same for my daughter :) )

---

### Post by vincentvee on 2006-09-08
yeah it seems to be a real problem at times

---

