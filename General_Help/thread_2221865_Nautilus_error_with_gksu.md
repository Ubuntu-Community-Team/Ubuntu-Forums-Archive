---
title: "Nautilus error with gksu"
date: 2014-05-04
forum: General Help
---

### Post by Greg_Kentwell on 2014-05-04
Hi all,

I'm getting the following error when open nautilus with gksu

**ThinkPad-X230:~$ gksu nautilus**

**(nautilus:3536): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'**
******
**ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))**

Is this a bug? How to solve it??
Any help appreciated
Cheers

---

### Post by pfeiffep on 2014-05-04
I just tested both gksu and gksudo nautilus on my Dell laptop with no problems
for your comparison ...
> pfeiffep@pete-dell:~$ uname -a
Linux pete-dell 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
pfeiffep@pete-dell:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

Please post the output of these commands run in a terminal you can access with ctrl-alt-t so we my better help you. 
```
uname -a
lsb_release -a
```

---

