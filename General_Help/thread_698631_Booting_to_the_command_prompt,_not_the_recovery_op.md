---
title: "Booting to the command prompt, not the recovery option."
date: 2008-02-16
forum: General Help
---

### Post by C. Wizard on 2008-02-16
I recently installed Kubuntu 7.10 amd64, and so far it is very impressive.

In Slackware, and other Linux distributions, there is a file by the name of, "inittab" that can be edited so you can boot straight to the command prompt or automatically fire up the GUI (KDE, Gnome, etc.).

I would like to be able to do this in Kubuntu (not the recovery option). Is this possible, and ,If so, what is the name of the file?

Thank you very much.

---

### Post by 444 on 2008-02-16
Looking in the /etc/event.d folder, it seems they still read the /etc/inittab file for compatibilty purposes, even though it's not there by default.

---

### Post by pointone on 2008-02-16
Simply remove or rename the symlink in /etc/rc2.d/S##gdm to prevent GDM from starting in the default runlevel (2). You can then start X easily by changing to runlevels 3 through 5.

---

