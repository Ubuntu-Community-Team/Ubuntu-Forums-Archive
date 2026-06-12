---
title: "New users without sudo?"
date: 2004-11-08
forum: General Help
---

### Post by v79 on 2004-11-08
Hi

Fairly Ok with the sudo root thing. But how do I stop certain users from accessing sudo? I don't want other users changing things! Is there a certain group which sudo users belong to, for instance?

Ta,

LJD

---

### Post by Juergen on 2004-11-09
I haven't tried to create more than my single user - are they really able to use sudo?
If yes, remove them from /etc/sudoers.
Or change their entry so that they can only use sudo with apps you want to allow, like maybe shutdown.

---

