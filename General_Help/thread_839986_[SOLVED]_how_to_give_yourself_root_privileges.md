---
title: "[SOLVED] how to give yourself root privileges"
date: 2008-06-24
forum: General Help
---

### Post by Kain000 on 2008-06-24
Hey all,
I am wondering how to give myself root privileges in the GUI, (I know the sudo command via the terminal)  to edit things I am told I need to be root to edit.  For example I am trying to enable sharing of a folder in my home network but am told that i need to be root.  I dont however want to run as root all the time for obvious security reasons.

thanks everyone.
-sean

---

### Post by jrusso2 on 2008-06-24
> **Kain000 said:**
> Hey all,
I am wondering how to give myself root privileges in the GUI, (I know the sudo command via the terminal)  to edit things I am told I need to be root to edit.  For example I am trying to enable sharing of a folder in my home network but am told that i need to be root.  I dont however want to run as root all the time for obvious security reasons.

thanks everyone.
-sean

I believe in Gnome you use gksu, I use kde so I use kdesu and then the name of the application.

gksu gedit

---

### Post by tamoneya on 2008-06-24
use gksudo: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Kain000 on 2008-06-26
Thanks guys, once again problem solved.

---

