---
title: "[SOLVED] Is there supposed to be a splash screen in Gutsy?"
date: 2007-10-25
forum: General Help
---

### Post by rainwalker on 2007-10-25
I've noticed both on the live CD and on my actual install, there's no splash screen after logging in.

Is this a problem? If it is, I need to know because I'm about to use said live CD to do a fresh install.

---

### Post by Aikon- on 2007-10-25
I believe it is setup like that by default; you can add a splash screen (there's a utility you can install from apt-get, but I don't remember the name), which I did, but I've noticed that it only stays up for a second or two and then goes away while the screen just sits there with a blank background until Xorg/Compiz finish loading.

---

### Post by rainwalker on 2007-10-25
Okay, good, I was kind of freaked out for a second

Thank you :)

---

### Post by por100pre1 on 2007-10-25
```
gnome-splashscreen-manager
```

To install it:

```
sudo apt-get install gnome-splashscreen-manager
```

---

