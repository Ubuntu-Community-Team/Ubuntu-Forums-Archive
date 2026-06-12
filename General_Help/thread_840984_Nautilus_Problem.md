---
title: "Nautilus Problem"
date: 2008-06-25
forum: General Help
---

### Post by gletob on 2008-06-25
Nautilus does not come up after I login but Gnome Panels do

running nautilus in the terminal results in
```
owner@glenn-laptop:~$ nautilus
/usr/lib/gio/modules/libgvfsdbud.so: file too short
Failed to load module: /usr/lib/gio/modules/libgvfsdbud.so
seahorse nautilus module initialized
Initializing nautilus-share extension
nautilus: symbol lookup error: /usr/lib/gio/modules/libgvfsdbus.so: undefined symbol: g_uri_get_scheme

```

---

### Post by gletob on 2008-06-26
1 hr bump

---

### Post by AmericanYellow on 2008-06-26
Apparently a missing module. Reinstall nautilus.

---

### Post by gletob on 2008-06-26
Reinstalling by
```
sudo aptitude reinstall nautilus
```
and
```
sudo apt-get remove nautilus
sudo apt-get install nautilus
```
do not work it still says 
```
owner@glenn-laptop:~$ nautilus
/usr/lib/gio/modules/libgvfsdbud.so: file too short
Failed to load module: /usr/lib/gio/modules/libgvfsdbud.so
seahorse nautilus module initialized
nautilus: symbol lookup error: /usr/lib/gio/modules/libgvfsdbus.so: undefined symbol: g_uri_get_scheme

```

---

