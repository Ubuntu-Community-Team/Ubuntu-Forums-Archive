---
title: "bigginer problems..."
date: 2008-05-08
forum: General Help
---

### Post by oriland on 2008-05-08
hi guys
i just joined the ubuntu family.
when the os start to run i get this message:
the networkmanager applet could not find some required resources. it cannot continue.

i don't know what does it mean...

i don't know if this is connected or not but most of the icons are gone, i only get a square with an X inside it.

help me!

thank
ori

---

### Post by latna on 2008-05-08
I've never seen this myself but a little googling revealed that some people have fixed it by entering this command into a terminal:```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```

HTH

---

### Post by oriland on 2008-05-08
i tried to use it but it doesnt fix the problem...
thanx anyway

---

### Post by oriland on 2008-05-08
when i write: sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
i get: 
gtk-update-icon-cache: No theme index file in '/usr/share/icons/hicolor/'.
If you really want to create an icon cache here, use --ignore-theme-index.

i really dont know what to do...

---

