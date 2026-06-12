---
title: "gutsy freez before shut down screen"
date: 2007-11-07
forum: General Help
---

### Post by carlos1992 on 2007-11-07
Hey need some help when i go system-->quit takes almost 1 minute to appear the shutdown screen i have made a couple tweak here and there disable powernowd and avahi-daemon and some more i don't really remember but since that the shutdown is sluggish:confused:

---

### Post by WIREHEAD on 2007-11-08
Carlos .

I have the same problem ( not much help )

I also made a few tweaks mostly to try to fix the splash screen .

Any of these look familiar  ? 
update-intramfs -u -k
dpkg-reconfigure -phigh usplash
update-alternatives  --config usplash-artwork.so
update-alternatives  --install <  too long to type > usplash-theme-fingerprint.so

Also installed/uninstalled via Synaptic ( in no particular order ) usplash , splashy , qingy , slim , grime .

Maybe someone can point us in the right direction ( It's not toward Windows ... )

I fully admit I'm a reckless newb with a penchant for tinkering with an otherwise functional system , teach me .

Thanks !

---

### Post by carlos1992 on 2007-11-08
mmm i didn't uninstall those but i don't have i dont know why but is really weird i saw this girl that had (well she has) the same problem, with similar tweaks

---

### Post by MicroChris on 2007-11-08
Did you disable Power Manager from startup? I did (thinking it was totally unrelated), and it was freezing my system from the Logout menu.

System > Preferences > Sessions

Under the Startup Programs tab, make sure Power Manager is checked.

---

### Post by WIREHEAD on 2007-11-09
Power manager is OK , enabled .

I'm thinking something to do with init scripts .
Somebody should probably stop me before I really screw something up ....

---

