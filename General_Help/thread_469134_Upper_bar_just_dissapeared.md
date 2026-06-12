---
title: "Upper bar just dissapeared"
date: 2007-06-09
forum: General Help
---

### Post by Anarkylfy on 2007-06-09
For some reason, my upper bar (the one you use to move the windows) just vanished. This is what I have now:

[IMG]http://img370.imageshack.us/img370/6007/windowvx4.jpg[/IMG]

How can I get it back? any ideas?

---

### Post by handaxe on 2007-06-09
Hi,

The following will restore both **DEFAULT** panels - your top one is lost AFAIK

At the CLI, type the following sequence, each line followed by an enter:

```
gnome-session-remove gnome-panel
 gconftool-2 --recursive-unset /apps/panel
gnome-panel &

```

HA

---

### Post by FuturePilot on 2007-06-09
I think the OP is talking about the window boarder. Try this
```
metacity --replace
```

---

### Post by handaxe on 2007-06-09
I now think you are right!

HA

---

### Post by figgles on 2007-11-10
Much thanks for the instruction on restoring default panels!

---

