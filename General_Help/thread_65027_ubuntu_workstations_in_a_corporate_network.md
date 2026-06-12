---
title: "ubuntu workstations in a corporate network"
date: 2005-09-12
forum: General Help
---

### Post by GOwin on 2005-09-12
i'm planning to migrate several departamental workstations and servers to Ubuntu.

some departments (departments may have 5 PCs to 25 PCs) would remain in Windows, while I also plan to deploy Wine in all the workstations. (there are still windows-based apps we need to run)

I'd like to know what's the most ideal solution? would there be any quick/easy solution? :D

Currently, our servers our mostly for Internet sharing and authentication and file/print sharing.

Almost all of our applications are desktop-based.

What do you think?

---

### Post by bsussman on 2005-09-12
Provided you research and test the functionality of MS apps under WINE - there is great variation in what works in what apps.  Some are perfect, some are non-starters.

---

### Post by GOwin on 2005-09-12
Let's just assume that they're likely to work since they're actually DOS-base apps, I'd like to know a quick and/or ideal way of deploying ubuntu.

I would also like to find out if it's possible to centralize the upgrades and/or software installation done on each workstation.

---

### Post by bsussman on 2005-09-12
[QUOTE=GOwin]Let's just assume that they're likely to work since they're actually DOS-base apps, I'd like to know a quick and/or ideal way of deploying ubuntu.[/QUOTE]
I dunno - that might be an ugly  assumption.

> I would also like to find out if it's possible to centralize the upgrades and/or software installation done on each workstation.
Not sure about centralized install but for upgrade, you might look at apt-catcher - I just found it and it claims to make the job of serving your own network for upgrades simpler.

---

### Post by GOwin on 2005-09-12
[QUOTE=bsussman]I dunno - that might be an ugly  assumption.


Not sure about centralized install but for upgrade, you might look at apt-catcher - I just found it and it claims to make the job of serving your own network for upgrades simpler.[/QUOTE]

I know, I know it's bad to make ANY assumption. Well, let's just say that our test workstations  don't show any major problems so far.  :)

Thin clients would be nice but we just have too much investments on full desktops right now. It would be a shame to waste those processing power.

---

### Post by GOwin on 2005-09-13
**bump** ;-)

---

