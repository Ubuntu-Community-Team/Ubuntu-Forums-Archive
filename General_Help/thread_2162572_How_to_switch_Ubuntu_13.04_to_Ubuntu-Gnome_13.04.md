---
title: "How to switch Ubuntu 13.04 to Ubuntu-Gnome 13.04"
date: 2013-07-15
forum: General Help
---

### Post by myocytebd on 2013-07-15
How to switch Ubuntu 13.04 to Ubuntu-Gnome 13.04?
I installed default 13.04 without knowing of Ubuntu-Gnome.

Unity is annoying and I want to get rid of it without reinstalling the system.

---

### Post by Cheesemill on 2013-07-15
```
sudo apt-get install ubuntu-gnome-desktop
```

If you are asked to chooses a display manager then select GDM. There is no need to remove Unity as it only takes up a few MB of drive space.

---

### Post by grahammechanical on 2013-07-15
If you are annoyed by Unity, then I do not think that Gnome 3 shell will be to your liking either.

---

### Post by ibjsb4 on 2013-07-15
Are you after the classic look?

```
sudo apt-get install gnome-session-fallback
```

And choose your desktop at login.

---

### Post by Frogs Hair on 2013-07-15
With Gnome installed choose the classic/fallback-session at log-in for a more traditional desktop. I would agree with the comment above regarding Unity.

---

### Post by 3rdalbum on 2013-07-15
Unity is good, but very different to anything else out there. I recommend giving it an honest try for a week, then you'll probably love it.

---

