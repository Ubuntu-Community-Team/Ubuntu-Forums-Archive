---
title: "Help, problem since upgrading to hardy."
date: 2008-06-23
forum: General Help
---

### Post by rideout on 2008-06-23
Hey, basically since I have updated to hardy. Everytime I open my home folder. The folder crashes and I cant access any of the folders inside it. Also when I try and quit the folder i get an error box saying wait or force quit.I click force quit and all it does is load the folder again and the same thing happens.

---

### Post by dracayr on 2008-06-23
open a terminal and type ```
ls -ld /home/*your username*
```

dracayr

---

### Post by rideout on 2008-06-23
that doesnt seem to work. It does nothing for me :(

---

### Post by dracayr on 2008-06-23
yeah, it shouldn't do anything, but it should give an output. post that here.

dracayr

---

### Post by Pjotr123 on 2008-06-23
Upgrade woes? Consider a clean reinstallation of 8.04.

A clean installation is always best, for all operating systems under the sun.

---

### Post by rideout on 2008-06-23
drwxr-xr-x 69 rideout rideout 4096 2008-06-23 09:38 /home/rideout


that is the output that i got

---

### Post by rideout on 2008-06-23
bump

---

### Post by danwood76 on 2008-06-23
Try listing the files within your home dir from the command line:
```

ls -ld /home/USERNAME/*

```

It might be some configuration file is causing your issues, you can move your gnome config files and force it to create a default set by running the following commands:
```

mv ~/.gnome ~/.gnome.bak
mv ~/.gnome2 ~/.gnome2.bak

```
Once you have moved them log out and log back in to see if its made a difference.

If it hasnt you can restore your original GNOME configs by doing the following:
```

rm -r ~/.gnome
rm -r ~/gnome2
mv ~/.gnome.bak ~/.gnome
mv ~/.gnome2.bak ~/.gnome2

```
Then log out and back in again.

---

### Post by rideout on 2008-06-23
none of that made a difference!

---

### Post by danwood76 on 2008-06-23
what was the output of the first command I said above?

---

### Post by rideout on 2008-06-23
haha randomly fixed it:) thanks dudes.

---

