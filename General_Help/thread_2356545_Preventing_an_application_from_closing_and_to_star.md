---
title: "Preventing an application from closing and to start if closed at all"
date: 2017-03-24
forum: General Help
---

### Post by alexander1989 on 2017-03-24
Ok, I have set an application to launch when my session starts, I need to prevent the user from closing the application and to re-launch if the application happens to close by other means

---

### Post by TheFu on 2017-03-24
Welcome to the forums.

Setup systemd to restart the application.
Or
setup a monitor that restarts the application if it isn't seen after 10 seconds - check every 10 seconds.
Or
run the application without a window as a different user, then the person sitting on the desktop won't be able to see it or have the idea it needs to be closed.  This would be the best way.

---

### Post by Impavidus on 2017-03-24
Sounds a bit like kiosk mode.

---

