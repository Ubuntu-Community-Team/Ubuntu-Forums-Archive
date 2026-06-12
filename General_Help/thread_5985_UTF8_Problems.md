---
title: "UTF8 Problems"
date: 2004-11-23
forum: General Help
---

### Post by ffub on 2004-11-23
[IMG]http://stomlinson.org/img/utf8-problems.png[/IMG] 

Is this an Ubuntu problem, or a GNOME problem?

---

### Post by daniels on 2004-11-24
[QUOTE=ffub]Is this an Ubuntu problem, or a GNOME problem?[/QUOTE]I suspect an Ubuntu problem; are you running Warty or Hoary?

---

### Post by rosvall on 2004-11-24
I was that same problem...Ubuntu couldn't so ä and ö letters... =) That was caused by wrong localisation.
Try to reconfig your locales, run:

sudo dpkg-reconfigure locales

---

