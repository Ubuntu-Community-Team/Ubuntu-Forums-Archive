---
title: "Script"
date: 2006-08-14
forum: General Help
---

### Post by xander848 on 2006-08-14
I have a script that has this line in the middle 
cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome login

Is there any way I can make it so that it will not prompt me for a password when it gets to this line. All that needs to happen is for me to press enter to login.

---

### Post by xander848 on 2006-08-15
anyone know?

---

### Post by mbeierl on 2006-08-16
I know that cvs will cache a password after initial login.  If the cvs pserver info is not dynamic (ie: if it is hard coded into the script and does not change) then you can avoid the login command altogether.  Simply logging in once will cache the login info into .cvspass and you should be good to go.

---

