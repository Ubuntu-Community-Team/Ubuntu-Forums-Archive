---
title: "Tomboy Notes startup"
date: 2008-06-17
forum: General Help
---

### Post by gos1 on 2008-06-17
Hi ; 
 
  I love the small program called Tomboy notes but only there is one problem . It does not start on startup. 
 
  I want it to start only when my user is logged in is it possible ?

---

### Post by wormser on 2008-06-17
You can add programs to start up with Session.  System> Preferences> Sessions and click Add.  The command for Tomboy Notes is tomboy.

---

### Post by gos1 on 2008-06-17
Thank you for your answer . This method is great . But I want to learn which file should I edit to change the startup programs too . I take a look at the /etc/init.d/rc.local but cannot find anything that I can change in it . Does anyone know which file is it ???

---

### Post by kpkeerthi on 2008-06-17
> **gos1 said:**
> Thank you for your answer . This method is great . But I want to learn which file should I edit to change the startup programs too . I take a look at the /etc/init.d/rc.local but cannot find anything that I can change in it . Does anyone know which file is it ???

GNOME keeps auto started settings in ~/.config/autostart folder. You'll find individual .desktop files in there.

---

