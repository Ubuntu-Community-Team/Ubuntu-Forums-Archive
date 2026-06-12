---
title: "Wubi Installation Twice Stuck At 74% While Storing Language!!"
date: 2007-08-21
forum: General Help
---

### Post by COMINAGETCHA! on 2007-08-21
Im trying to install Ubuntu with Wubi and twice the base system installation got stuck at 75% as its storing language.  There is a similar message in the forum and they fixed the problem with re-writing cd at slower speed.  If thats the solution why does this problem occur when Im installing using Wubi, which uses the hard disk for installation.

---

### Post by ago on 2007-08-21
Do you have more than 256MB memory?

---

### Post by COMINAGETCHA! on 2007-08-21
Unfortunately I have only 256MB memory. Is it requried to be more than that to install Ubuntu?

---

### Post by ago on 2007-08-21
That's  borderline. It's fine to use it (particularly with xfce), but sometimes it can create problems during installation and particularly with wubi (since wubi installer it's more memory hungry). One way around it is not to install the desktop environment (edit wubi/install/preseed.cfg and select ubuntu-standard as opposed to ubuntu-desktop) and install the desktop environment at first boot as a separate step (sudo apt-get install xubuntu-desktop).

---

### Post by smilesfozwood on 2007-09-26
I've had the same problem, but how do you edit wubi/install/preseed.cfg? I can't even find it! I'm kindof a noob...

---

