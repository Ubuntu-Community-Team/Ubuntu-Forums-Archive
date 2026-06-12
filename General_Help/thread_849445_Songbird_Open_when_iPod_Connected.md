---
title: "Songbird Open when iPod Connected"
date: 2008-07-04
forum: General Help
---

### Post by GuitarRocker2562 on 2008-07-04
Everytime I connect my iPod, Rythembox opens, how do I change it so Songbird opens.

---

### Post by GuitarRocker2562 on 2008-07-04
anybody?

---

### Post by GuitarRocker2562 on 2008-07-04
seriously?

---

### Post by Double D on 2008-08-30
havent found a solution for this either

Nautilus > Edit > Preferences > Media 
doesnt give you an option to browse for a different command other than what is listed

---

### Post by fwre01 on 2008-08-30
i can choose banshee aswell as rythmbox. But we must be able to add to that list in a config file somewhere

---

### Post by Tom--d on 2008-08-30
Remove Rhythmbox

```
sudo apt-get remove rhythmbox
```

---

### Post by fwre01 on 2008-08-30
i did a few tests with the udev rules files and i managed to get a script to run when a certain device (i.e my ipod) was plugged in. i wanted the script to run a different program, but it didnt seem to work, nothing happened when it got plugged in. i changed the script to touch a file in /tmp and this did work!

maybe someone can tell me why my script wouldnt run the program, but would touch a file.

(When i ran the script manually from the cli the program would open)

This is the line i added to /etc/udev/rules.d/80-programs.rules

KERNEL=="sdc2", RUN+="~/bin/run_easytag"

---

### Post by Double D on 2008-09-01
> **Tom--d said:**
> Remove Rhythmbox

```
sudo apt-get remove rhythmbox
```

This doesnt make songbird become an option

---

