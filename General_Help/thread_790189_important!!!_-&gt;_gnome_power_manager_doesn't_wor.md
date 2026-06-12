---
title: "important!!! -&gt; gnome power manager doesn't work and apps too"
date: 2008-05-11
forum: General Help
---

### Post by biasquez on 2008-05-11
hi, i'm running ubuntu 8.04. until last week, ubuntu works fine but  now, always or ever system starts and gnome-power-manager icon doesn't start in tray. so, if i try to launch it from terminal, i don't have any  output, idem if i try to launch apps like firefox or gnome-terminal, no output and nothing works. is it problem with dbus or permission's home or others? support plz

---

### Post by mardawi on 2008-05-11
This might be a permession problem, so restart and once grub appears hit Esc then choose recovery mode (should be second option)

This will give you a terminal root access. to check if you have admin permissions write:

```
groups user-name
```

it should say "admin" within the output, if it doesn't, add your user-name to admin group by:
```
adduser user-name admin
```

---

### Post by biasquez on 2008-05-11
i have admin permissions but problem is unsolved. i'm trying a mode to debug and see some error but i don't have any idea how to check these errors.

---

### Post by biasquez on 2008-05-12
problem SOLVED removing folder .gnome*

---

