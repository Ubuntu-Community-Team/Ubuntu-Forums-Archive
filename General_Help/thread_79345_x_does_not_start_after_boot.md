---
title: "x does not start after boot"
date: 2005-10-20
forum: General Help
---

### Post by soonindallas on 2005-10-20
when I booted today I was presented with the CL login request instead of Gnome.

If I login and issue "startx" command, Gnome starts and I have my desktop.  However Gnome system > log out does not offer me shutdown, hibernate etc options, only "log out" that puts me back at the command line and I need to issue the shutdown command there.

How can I troubleshoot this ?

---

### Post by codejunkie on 2005-10-20
[quote=soonindallas]when I booted today I was presented with the CL login request instead of Gnome.

If I login and issue "startx" command, Gnome starts and I have my desktop.  However Gnome system > log out does not offer me shutdown, hibernate etc options, only "log out" that puts me back at the command line and I need to issue the shutdown command there.

How can I troubleshoot this ?[/quote]
did you remove the package gdm?

---

### Post by soonindallas on 2005-10-20
[QUOTE=codejunkie]did you remove the package gdm?[/QUOTE]

thanks for the speedy reply.  synaptic shows package gdm is absent.  looking at synaptic history for yesterday I notice:

```
Commit Log for Tue Oct 18 14:32:54 2005

Removed the following packages:
gdm
ubuntu-sounds

Installed the following packages:
gnome-audio (2.0.0-2)
```

lack of attention on my part.  thanks again.

---

### Post by soonindallas on 2005-10-20
curiously when I select gdm for installation, synaptic tells me it needs to remove gnome-audio and install ubuntu-sounds.

does this mean gdm and gnome-audio cannot coexist ?  this seems counter-intuitive.

---

