---
title: "[SOLVED] GDM not running"
date: 2008-06-11
forum: General Help
---

### Post by Peter09 on 2008-06-11
After messing around trying to configure x11vnc (which I've sorted) I find that I am booting into a text prompt rather than the normal login screen. A command line login plus startx gets everything going again.

When I do

 > System->Administration->Login Window

I get a message telling me that GDM is not running. 

Can anyone point me to how to get GDM running again.

Thanks

---

### Post by AlbertTatlocksCap on 2008-06-11
Ok try this in a terminal ..

sudo etc/init.d/gdm start

Hope it helps

---

### Post by iaculallad on 2008-06-11
Open the default-display-manager file:

```
sudo gedit /etc/X11/default-display-manager
```

Content should be like this:

> /usr/sbin/gdm

---

### Post by Peter09 on 2008-06-11
Thanks for the help,
discovered that /etc/X11/default-display-manager file was pointing to /etc/bin/gdm rather than /etc/sbin/gdm

PC

---

