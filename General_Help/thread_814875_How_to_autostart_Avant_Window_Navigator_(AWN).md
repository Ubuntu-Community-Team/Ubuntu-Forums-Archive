---
title: "How to autostart Avant Window Navigator (AWN)?"
date: 2008-06-01
forum: General Help
---

### Post by D.Sync on 2008-06-01
Any ideas on how to do so? I don't want to manually open the application each time I open my computer.

Thanks for the answer.

---

### Post by raiwo on 2008-06-01
system->preferences->sessions-> add new startup program

---

### Post by D.Sync on 2008-06-01
But what command name should I type? avn --replace?

---

### Post by trevelyan on 2008-06-01
> **D.Sync said:**
> Any ideas on how to do so? I don't want to manually open the application each time I open my computer.

Thanks for the answer.

like this:
go to System then preferences and then sessions
on the "starup programs" tab do this:
click add, (and the "add startup program" window appears.) fill it out like this:
Name: Avant Window Navigator
command: avant-window-navigator
comment: Avant Window Navigator

actually, name and comment can be anything you want like AWN :)

---

### Post by D.Sync on 2008-06-01
Thanks much for the info! Really fast reply~

---

### Post by trevelyan on 2008-06-01
no problem :D

---

### Post by Prospero2006 on 2008-06-01
I also like to eliminate the gnome panel.

mv /usr/bin/gnome-panel /usr/bin/gnomepanelbackup

---

### Post by scrypt on 2009-03-27
> **Prospero2006 said:**
> I also like to eliminate the gnome panel.

mv /usr/bin/gnome-panel /usr/bin/gnomepanelbackup

Just Delete the panel. by right clicking on it then selecting Delete

scrypt

---

