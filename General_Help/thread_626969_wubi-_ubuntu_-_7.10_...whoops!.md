---
title: "wubi- ubuntu - 7.10 ...whoops!"
date: 2007-11-29
forum: General Help
---

### Post by brosville on 2007-11-29
I did something daft - having become enamoured of Ubuntu installed by Wubi, I absent mindedly clicked the ~"upgrade to 7.10" button in the ~"update" section...........it did! Works fine except "hal" doesn't want to play - any easy quick fixes?
(short of repartitioning, reinstalling etc)
ps, I'm a "point and clicker", not an expert!

---

### Post by ago on 2007-11-29
Hmm it's gonna be difficult to be able to boot from there... You can try to downgrade the hald package.

---

### Post by brosville on 2007-11-30
if it's not a daft question - how do I do that?:(

---

### Post by brosville on 2007-11-30
trawled a few threads, and used synaptic to install the older version- still the same!:(

---

### Post by brosville on 2007-12-02
bump!:)

---

### Post by brosville on 2007-12-02
I have a feeling I'm getting close............when I restart dbus, part of the output is
" * Starting Hardware abstraction layer hald   run-parts: /etc/dbus-1/event.d/hal exited with return code 1":(

---

### Post by ago on 2007-12-03
It's probably easy to try a new installation, move the home virtual disk somewhere else, uninstall wubi, install wubi 7.10, then after installation move the home disk it to /ubuntu/disks so you can copy the content

---

### Post by brosville on 2007-12-03
thanks! - probably easier than "tinkering":)

---

