---
title: "How to kill gnome"
date: 2005-10-15
forum: General Help
---

### Post by billiejoex on 2005-10-15
Hi all. On other linux distributions I always killed the desktop session by pressing CTRL+ALT+DEL.
On Ubuntu linux this produce a restart. 
How can I definitely kill my desktop session?
Moreover how can I avoid that Gnome\KDE automatically starts up on every boot?

Thanks in advance.

---

### Post by JediPottsy on 2005-10-15
sudo killall gnome-panel nautilus

---

### Post by billiejoex on 2005-10-15
Thank you. Do you know the same for KDE?

---

### Post by xmastree on 2005-10-15
> On other linux distributions I always killed the desktop session by pressing CTRL+ALT+DEL.You sure about that? It's usually **Ctrl-Alt-Backspace**.

---

### Post by billiejoex on 2005-10-15
Yes, I'm sorry: backspace.
What about my second question?
Does somebody knows how can I avoid Gnome/KDE auto start up?

---

### Post by chaumurky on 2005-10-15
Yep. It just looks like a restart. But then...

---

### Post by strips on 2005-10-15
[QUOTE=JediPottsy]sudo killall gnome-panel nautilus[/QUOTE]

That only kills the panel and nautilus.


```
sudo /etc/init.d/gdm stop
```

This stops the gdm daemon that automatically restarts X after you kill it with Ctrl-Alt-Backspace

---

