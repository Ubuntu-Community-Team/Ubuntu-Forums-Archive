---
title: "gnome-software can't install anything from XFCE, only works in Gnome"
date: 2020-03-27
forum: General Help
---

### Post by u666sa on 2020-03-27
Ubuntu 18.04

Basically everything works fine in Gnome.  You go to gnome-software, select a program to install, it asks you for root password and does it thing.

however...

In XFCE this does not work.  You are not asked for password, an error is given, not enough privileges.  You have to launch it with sudo from terminal, only then it works.  

What to do and how to fix this?

---

### Post by u666sa on 2020-03-27
Solution was to install [COLOR=#242729][FONT=Consolas]sudo apt install synaptic apt-xapian-index policykit-1-gnome [/FONT][/COLOR]

---

