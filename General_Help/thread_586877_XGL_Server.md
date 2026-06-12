---
title: "XGL Server"
date: 2007-10-22
forum: General Help
---

### Post by gavinjb on 2007-10-22
Hi,

my Laptop runs an ATI graphics card, so to run Compiz I needed to install XGL-Server, only problem is that I can no longer select XGL if I want to use it from sessions, as it automatically starts if installed and this is unusable for me, as when I want to play games like GuildWars I get 4-5 fps with Xgl and 20+ without and I want to be able to default to XGL, but those times when I want to play games logon without XGL, does anyone know how I can do this with Gutsy.

Thanks,



Gavin,

---

### Post by ajgreeny on 2007-10-22
Make another user called games and set that user not to use xgl?  That should be the way, surely.

---

### Post by gavinjb on 2007-10-23
Thanks, only problem is I would have to re-install my games as most of the Games are running under wine, does anyone know if I can configure the sessions in the logon screen so, I can choose either Gnome or Xgl like I have setup previously on Feisty (cant remember how I did this).

Thanks,


Gavin,

---

### Post by jdefaver on 2007-10-23
You can launch your games with the command "DISPLAY=:0 mygame" in order to override XGL. Works well for me.

---

