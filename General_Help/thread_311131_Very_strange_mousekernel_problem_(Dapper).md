---
title: "Very strange mouse/kernel problem (Dapper)"
date: 2006-12-02
forum: General Help
---

### Post by null_pointer_exception on 2006-12-02
I have recently moved to Ubuntu from Gentoo. I tried Edgy, but got kernel panics etc at boot so decided to try Dapper. However, I have a very strange problem with the mouse.

The system boots and I can log in, and everything seems to be fine, but when I click on anything, nothing happens. Then, if I move the mouse, things begin to happen es expected. For example, if i select a menu item, nothing happens untill I move the mouse, and then the application is launched. If i open settings, alter them and click OK, nothing happens untill I move it again. Mouse movement is not required for action such as opening a menu, context menus, selecting desktop items.

My arch is AMD64, which may be the problem, and this is a laptop with a touchpad. The problem does not occur with a USB mouse; only the touchpad. The same problem happent in Kubuntu.

Any ideas are welcome, and thanks in advance.

---

### Post by null_pointer_exception on 2006-12-21
Wow. Anyway, enabling SMConfig seemed to fix it.

---

