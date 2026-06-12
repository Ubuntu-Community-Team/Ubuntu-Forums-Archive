---
title: "User and Group Administration via GUI"
date: 2020-06-10
forum: General Help
---

### Post by zeekstern on 2020-06-10
I'm trying to get the GUI for managing users and groups. 
I found where the package name is gnome-system-tools. 
I end up with this when trying to install it:

```
sudo apt-get install gnome-system-tools
Reading package lists..   Couple more things.. and then

E: unable to locate package gnome-system-tools
```

I found it at package.ubuntu.com/focal/amd64/gnome-system/download. 
The website says to use aptitude or synaptic to download and install packages.
I'm assuming that aptitude is the apt command I used to try to install it:))

 Any help is appreciated. 


Zeek

---

### Post by deadflowr on 2020-06-10
gnome-system-tools should be in the Community (universe) repository, so check that it is enabled in Software and Updates.
By default Ubuntu only enables the Canonical (main archives) and Proprietary (restricted  archives).

---

### Post by zeekstern on 2020-06-11
Thanks Deadflowr. That worked just fine.

Zeek

---

### Post by ActionParsnip on 2020-06-11
If you learn to use the command line you can manipulate users in any Linux distribution on any system. This is a transferable skill rather than a GUI which may or may not be installed.

---

### Post by zeekstern on 2020-06-11
Thanks ActionParsnip. I do know the command line and actually prefer it. I am weak on Gnome and other Desktop stuff. I'm an ex Solaris guy:))

---

