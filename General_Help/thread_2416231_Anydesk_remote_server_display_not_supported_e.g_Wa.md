---
title: "Anydesk remote server display not supported e.g Wayland"
date: 2019-04-07
forum: General Help
---

### Post by konstantinos4 on 2019-04-07
Hi all,
I downloaded Anydesk (4.0.1 64bit) both to my laptop and desktop and when I run it from one pc and try connect to the other I get the error
**remote server display not supported e.g Wayland.**
Both pcs' run Ubuntu 18.04.2.
I tried search for a solution, I found a suggestion to disable Wayland in the file **/etc/gdm3/custom.conf **
setting **WaylandEnable=false** but nothing changed.

Any help? :sad:

---

### Post by TheFu on 2019-04-07
Before you login, there is a "gear" icon on the login screen.  Click it and choose the X11 or non-Wayland option, then login.

---

