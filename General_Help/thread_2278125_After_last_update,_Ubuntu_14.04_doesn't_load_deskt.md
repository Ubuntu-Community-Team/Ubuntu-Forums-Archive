---
title: "After last update, Ubuntu 14.04 doesn't load desktop (metacity)"
date: 2015-05-14
forum: General Help
---

### Post by trallallero on 2015-05-14
If I login with metacity session, desktop is not loaded and nothing is shown.
I have to ctrl+alt+f1 to open a shell, kill lightdm, restart lightdm, login with gnome session, logout and and login again with metacity.

What could be the problem ?

---

### Post by iojedaperez on 2015-05-14
Few info to know what could be the problem, but its clearly related to a misconfig or bug in lightm, so i suggest you to install gdm instead as display manager
sudo apt-get install gdm
once you do that select gdm as default login manager and your problem will be solved.

---

### Post by trallallero on 2015-05-14
Ok, switched to gdm and everything is just the same.
but
There is a "system default" in the list of sessions and choosing this works.
but
There's no minimize, maximize and close buttons anywhere.

Thanks iojedaperez, now I try to solve this new problem.

---

### Post by trallallero on 2015-05-14
Ok, fixed.
"Window decoration" was disabled in compiz config.
I could say "problem solved" but I'd like to know what is causing this problem.
Anyways, thanks again

---

### Post by iojedaperez on 2015-05-14
you are welcome, please mark this as solved so more people can bennefit from the solution.

---

### Post by trallallero on 2015-06-10
AGAIN! updated, login, nothing! killall gdm, started lightdm, login, nothing! login with other session, logout, login with metacity, ok.

How long will this go on ? will it happen at every ubuntu update ?

---

