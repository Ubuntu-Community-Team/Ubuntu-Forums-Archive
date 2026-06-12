---
title: "No drag and drop (to dekstop ) on Ubuntu 20.04  why ????"
date: 2020-12-14
forum: General Help
---

### Post by jedi123 on 2020-12-14
Hi , how come in Ubuntu 20.04  dragging and dropping to the desltop is diabled? Thanks

---

### Post by tea for one on 2020-12-15
Are you familiar with [https://extensions.gnome.org/](https://extensions.gnome.org/)

Perhaps this [https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/) will be suitable.

---

### Post by deadflowr on 2020-12-15
> **jedi123 said:**
> Hi , how come in Ubuntu 20.04  dragging and dropping to the desltop is diabled? Thanks

> **tea for one said:**
> Are you familiar with [https://extensions.gnome.org/](https://extensions.gnome.org/)

Perhaps this [https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/) will be suitable.

To add some context,
The desktop used to be handled by the file manager,
but between 18.04 and 20.04 the file manager removed the feature that handled the desktop.
But because so many users rely on icons on the desktop, they created the desktop-icons gnome extension.
But the version shipped with Ubuntu is the original.
While stable it certainly lacks in features.

Luckily (depending on your point of view) the desktop-icons creator has also created the above fork, which has better features.
There is a discussion about possibly moving Ubuntu to use said fork over at discourse:
[https://discourse.ubuntu.com/t/desktop-icons-integration-problems/14577]("https://discourse.ubuntu.com/t/desktop-icons-integration-problems/14577")

---

