---
title: "'shutdown' disappeared from the exit dialog"
date: 2006-11-17
forum: General Help
---

### Post by bricedebrignaisplage on 2006-11-17
I am in Gnome. I think it's since I installed KDE. Now I also have a KDE login window. When I click on the small door at the top-right corner, 'shutdown' doesn't appear  in the dialog.
How can I restore it?

Brice

---

### Post by computx on 2006-11-17
Does your system still automatically start xwindows at boot or do you need to type startx first?

if you pick logoff does the login manager return and have an option to shutdown/restart?

---

### Post by ser1alsn1per on 2006-11-17
if you are using beryl/compix the shutdown button is removed I think it causes problems

---

### Post by computx on 2006-11-18
Hmm, I use beryl and the shutdown button is still visible on my pc.

---

### Post by Jimmy_r on 2006-11-20
As I understand it, your current display manager is kdm.
If Kdm is default, it wont let gnome manage shutdown.
If Gdm is default, it wont let kde manage shutdown.

I do not know if there is a way around this.

If you want gdm in charge again, try the command:
```
sudo dpkg-reconfigure gdm
```

I do only have gnome installed right now, however, so i can not test it.

---

### Post by bricedebrignaisplage on 2006-12-06
That was exactly what I needed. Thanks Jimmy_r.

---

