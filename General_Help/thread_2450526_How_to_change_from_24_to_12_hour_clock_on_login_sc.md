---
title: "How to change from 24 to 12 hour clock on login screen?"
date: 2020-09-15
forum: General Help
---

### Post by ihavenoname123 on 2020-09-15
How can I change this on the login screen? It is Lubuntu 20.04..thanks!

I found this [https://askubuntu.com/questions/1043364/clock-on-login-screen-in-24-hour-format-desktop-in-12-hour-format-18-04-upgrad/1046753#1046753](https://askubuntu.com/questions/1043364/clock-on-login-screen-in-24-hour-format-desktop-in-12-hour-format-18-04-upgrad/1046753#1046753)
but I don't think it applies here

---

### Post by guiverc on 2020-09-15
Lubuntu 20.04 LTS uses `sddm` as it's greeter (login screen & display manager).

The Lubuntu manual page can be found at [https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html](https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html)

Currently there is no easy GUI tool to edit it; that's still being perfected :)

Other wikis also exist of course laying out options, as the Lubuntu manual only briefly touches on the topic (a common complaint about the manual was too technical, so that detail is avoided), and example of a wiki available includes

[https://github.com/sddm/sddm/wiki](https://github.com/sddm/sddm/wiki)
[URL="https://wiki.archlinux.org/index.php/SDDM"]https://wiki.archlinux.org/index.php/SDDM


*FYI: No the ask ubuntu link won't help, it assumes `lightdm` as used by 18.04. The `sddm` configuration on 18.04 is almost identical, but it wasn't used before 18.10 by Lubuntu.*
[/URL]

---

### Post by ihavenoname123 on 2020-09-15
I will check into all of that..thanks for your help

UPDATE: bypassed the login screen on startup..good enough

---

