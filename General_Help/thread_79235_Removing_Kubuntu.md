---
title: "Removing Kubuntu"
date: 2005-10-19
forum: General Help
---

### Post by ecobuntu on 2005-10-19
Hi I am trying to remove KDE from my computer.  How do I do this?  

I've tried....


sudo apt-get remove kubuntu-desktop
  
and

sudo apt-get remove kde

They don't work.
Anyone know?

---

### Post by paulvandenberg on 2005-10-19
Try removing kdelibs. Go into Synaptic and search for it. If you remove that, all KDE apps will be removed as well.

Paul

---

### Post by rattaro on 2005-10-19
I have to first ask what you are trying to do.  Are you trying to change it to gnome based Ubuntu?  Are you trying to delete the whole OS and start new?  There are different approaches, depending upon your end goal.

---

### Post by ecobuntu on 2005-10-19
I am already running gnome.  I just dont' want to use KDE.

---

### Post by ecobuntu on 2005-10-19
Also I would like to do it the proper way so that I don't have a ton of extra configuration files left on my computer.  I just want to run gnome not kde.  
thanks

---

### Post by ecobuntu on 2005-10-19
[QUOTE=paulvandenberg]Try removing kdelibs. Go into Synaptic and search for it. If you remove that, all KDE apps will be removed as well.

Paul[/QUOTE]

FYI - This worked and I deleted KDE.

---

