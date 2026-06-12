---
title: "Ubuntu Server gui"
date: 2006-10-02
forum: General Help
---

### Post by coolduder8 on 2006-10-02
Hello,
I just installed Ubuntu Server. After booting into the server and logging in, how do i get to the Graphical User Interface (which i believe is gnome)?

---

### Post by aysiu on 2006-10-02
The server is intended to not have a graphical user interface.

If you are running a server, Gnome may be a bit resource intensive. How about something like IceWM or Fluxbox? ```
sudo aptitude update
sudo aptitude install icewm gdm
sudo /etc/init.d/gdm start
```

---

