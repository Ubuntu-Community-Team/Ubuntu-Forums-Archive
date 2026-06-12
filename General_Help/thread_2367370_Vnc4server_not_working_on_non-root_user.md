---
title: "Vnc4server not working on non-root user"
date: 2017-07-29
forum: General Help
---

### Post by przemek7 on 2017-07-29
I am trying to start vncserver on non-root user but it fails. It works on root. Here is log file: [http://pasteonline.org/izrfwejDG/](http://pasteonline.org/izrfwejDG/)

I tried to fix it by adding this line to user-dirs.dirs file but it didn't help:
XDG_RUNTIME_DIR="/run/user/$uid"

---

### Post by TheFu on 2017-07-30
I don't know anything about vncserver. Don't use it.
The general solution to any Linux issue is to check the log files for any warnings or errors, then address each from the oldest to the newest until the issue is fixed.  "Linux log files" as a search term will help you find and search the logs on your system.

VNC isn't often the best solution, btw.

---

