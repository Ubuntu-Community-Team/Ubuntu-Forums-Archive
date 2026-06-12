---
title: "Apache Control Applet?"
date: 2007-06-08
forum: General Help
---

### Post by Jamie Jackson on 2007-06-08
In Windows, Apache 2.2 installs with a handy control applet in the system tray: Click the icon and stop/start/restart Apache (IIRC).

I'm looking for a way to stick an icon in my top Gnome bar that I can control Apache from. (Or some thing similar.)

Thanks,
jamie

---

### Post by kidders on 2007-06-29
Hi there,

Starting & stopping Apache is trivial (ie a single command). Perhaps you could create a launcher of some sort?

---

### Post by trak87 on 2007-06-29
Perhaps you could create a couple of launcher buttons, one to start and one to stop apache:

```
gksudo /etc/init.d/apache2 start
```

```
gksudo /etc/init.d/apache2 stop
```

This is untested, but it should prompt you for a password.

---

### Post by Jamie Jackson on 2007-07-01
Whoops,  I lost track of this thread. I did end up creating a new launcher for "restart apache", which does both of these commands in a row.

Works for me! Thanks for the responses.

---

