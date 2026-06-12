---
title: "Problem running gnome programms in kubuntu 6.10"
date: 2006-12-07
forum: General Help
---

### Post by melonipoika on 2006-12-07
Hi all,

I am getting this error when I try to run a gnome programm in kubuntu:

symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

I have had this error with gizmo, alexandria, amule... I tried reinstalling and reconfiguring libfreetype, libcairo, etc. without success.

Does someone know how to solve this error? Thanks for your help in advance!

---

### Post by taurus on 2006-12-07
How did you install those Gnome apps?  Did you do something like

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

