---
title: "Update notifcations set to 'never', but am getting update notifications"
date: 2018-11-12
forum: General Help
---

### Post by aeronutt on 2018-11-12
Uggg...this makes me angry. My Ubuntu is starting to feel like some of those other OS's. I have update notifications set to 'Never', yet a GUI update notification just popped up.

What am I missing?

[https://i.imgur.com/zsymtO2.png](https://i.imgur.com/zsymtO2.png)

---

### Post by aeronutt on 2018-11-15
Any ideas?

---

### Post by Impavidus on 2018-11-16
You can set the update manager to never check for updates automatically, but can't set it to never notify you of updates (at least, not without removing the update manager). If you never check for updates, it won't notify you, but if you manually check for updates, it will notify you repeatedly until you install them. Or you can set the security updates to install automatically.

Of course, unless you have some very special case, it's best to install those updates right away.

---

### Post by aeronutt on 2018-11-18
Thanks for the clarification, from a logical viewpoint that makes sense. It would be nice to be able to turn all that off. 
I checked, and I can't remove update-manager without removing ubuntu-desktop.

---

### Post by mc4man on 2018-11-18
> **aeronutt said:**
> Thanks for the clarification, from a logical viewpoint that makes sense. It would be nice to be able to turn all that off. 
I checked, and I can't remove update-manager without removing ubuntu-desktop.

The ubuntu-desktop package is just a meta package that thru it's dependencies & recommends installs  packages that  make up the default ubuntu . It by itself can be safely removed. 
(the main value post install of the ubuntu-desktop package is it should be installed if doing an in place upgrade to next release of Ubuntu.

Here I always remove update-manager, update-notifier & unattended-upgrades with no issues whatsoever.

---

### Post by aeronutt on 2018-11-18
Thanks! Excellent, marked as solved.

---

