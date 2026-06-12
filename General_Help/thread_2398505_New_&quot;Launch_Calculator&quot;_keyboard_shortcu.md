---
title: "New &quot;Launch Calculator&quot; keyboard shortcut doesn't work"
date: 2018-08-13
forum: General Help
---

### Post by glubbdrubb on 2018-08-13
I created a new keyboard shortcut using the built in utility in 18.04
I assigned it to Super+c
But the shortcut doesn't work. the calculator isn't launched.

Help?

---

### Post by mc4man on 2018-08-13
This is because you're likely using the snap version of gnome-calculator.
To make shortcut work
```
sudo apt install gnome-calculator
```
If that's suitable & you don't want 2 versions then
```
sudo snap remove gnome-calculator
```

---

### Post by glubbdrubb on 2018-08-13
The fist command worked. Thank you!

Shall I submit this as a bug? Since this functionality should work straight out of the box. This is a new install, after all.

---

### Post by corradoventu on 2018-08-13
The bug on Gnome calculator is already known, they are some bug about:
[https://forum.snapcraft.io/t/gnome-calculator-failed-to-create-symbolic-link/5742](https://forum.snapcraft.io/t/gnome-calculator-failed-to-create-symbolic-link/5742)
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622)
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1785388](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1785388)

---

### Post by glubbdrubb on 2018-08-13
Ah interesting. Thanks

---

