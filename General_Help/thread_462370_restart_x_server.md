---
title: "restart x server"
date: 2007-06-02
forum: General Help
---

### Post by gulmer on 2007-06-02
I was tweeking system settings and I was trying to change the refresh rate from 60 to 85, moniter recomemded rate, but there was no setting for 85Hz, just 60Hz. After I hit "apply" for the changes I made a window popped up saying I needed to log out and back in, and in menu? "restart x server"   for the changes to take effect. What menu and where is the "restart x server" at?   Thanks Gene  [IMG]http://file:///home/gulmer/ubuntu-user2.png.gif[/IMG]

---

### Post by mrcbrown on 2007-06-02
You can logout, and log back in, should do it, as it should drop you to GDM and restart X11 in the process - other option would be to reboot entirely.

---

### Post by blackened on 2007-06-02
Dropping back to GDM doesn't restart the xserver. To do this you would either use
```
sudo /etc/init.d/gdm restart
```
or, failing that, ctrl-alt-backspace to kill the xserver and let it restart itself.

---

### Post by steveneddy on 2007-06-02
> **blackened said:**
>  ctrl-alt-backspace to kill the xserver and let it restart itself.

My favorite way.

---

### Post by blackened on 2007-06-02
> **steveneddy said:**
> My favorite way.

It's my favorite way when I'm angry, all other times I use gdm restart.

---

