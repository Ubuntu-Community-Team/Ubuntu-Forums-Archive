---
title: "gnome-keyring taking my whole RAM"
date: 2015-02-19
forum: General Help
---

### Post by Marcos_Bacon on 2015-02-19
Any ideas why gnome-keyring is taking so much memory?

[ATTACH=CONFIG]260089[/ATTACH]

---

### Post by dino99 on 2015-02-19
you might have something (an app request in the background for example) in a loop.
Start by closing all the opened apps, then log out/in and proceed step by step to narrow down the faulty process

---

