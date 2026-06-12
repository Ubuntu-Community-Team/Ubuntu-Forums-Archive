---
title: "White Box in top left when logging into Gnome"
date: 2008-01-20
forum: General Help
---

### Post by kthxbai2u on 2008-01-20
My desktop (Gnome) wont load. There is a white rectangle that is almost a quarter of the screen stuck in the top left corner of the blank desktop.

I've seen other threads similair to this. One of them was apparently solved by installing 32 bit edition (which i have). The other one was when the desktop was loaded, there was this tiny grey rectangle covering part of the menu. These are not related.

I tried using apt-get to remove and install gnome and gdm. gnome was not installed, so I installed it. gdm was, so I reinstalled it.

That hasnt solved the problem, and I'm sure that method would also remove and replace the configuration files? So it must mean it isnt a GDM or Gnome configuration problem. KDM and KDE work fine O_o


any ideas :confused::confused::confused:

---

### Post by mcs1 on 2008-04-09
Same here since yesterdays update of hardy.
On a fresh login, the desktop is just not responsive at all. The only thing that can be done is restart the X-server.
I have got an intel 965 card, which alwasy caused problems, maybe that is the culprit. I think there was a driver update yesterday.

Cheers

MCS

---

### Post by mcs1 on 2008-04-10
Found the problem
package libesd-alsa0 causes gnome to hang. Installed libesd0 instead, and it works. I can also kill esd -nobeeps and it works. Replacement with libesd0 results in **** sound and no system sounds, but better than nothing at all :).
with libesd-alsa0:
Once killed I  can do ctrl-alt-bkspace and often one can login without trouble. Often it does not work and esd has to be killed again.


Hope that helps someone 

Cheers

MCS

---

