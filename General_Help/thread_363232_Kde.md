---
title: "Kde"
date: 2007-02-16
forum: General Help
---

### Post by Touch.Code on 2007-02-16
Hey,

Earlier on today I installed KDE:

```

sudo apt-get install kubuntu-desktop

```

It changed my bootscreen, but I don't know what else has changed. When I login its the GNOME environment. It doesn't matter if it's messed my Laptop up, I will just re-install 6.10! 

Touch

---

### Post by jabeez on 2007-02-16
You need to log-out, and from the log-in screen click "Sessions" and pick KDE. Enjoy.

---

### Post by old_geekster on 2007-02-16
It will also allow you to try the new desktop without making the change permanent.

---

### Post by ButteBlues on 2007-02-16
> **jabeez said:**
> You need to log-out, and from the log-in screen click "Sessions" and pick KDE. Enjoy.
Yup.

If you find you like KDE more, you can also change to the KDE login screen (instead of the GNOME one) by running:

```
sudo dpkg-reconfigure kdm
```

and selecting kdm when the dialog appears.

---

### Post by Touch.Code on 2007-02-17
Thanks. Im guessing if I want to change back to GNOME then I replace Kdm gnome right?

---

### Post by ButteBlues on 2007-02-17
> **Touch.Code said:**
> Thanks. Im guessing if I want to change back to GNOME then I replace Kdm gnome right?
You don't have to, no. To decide between KDE and GNOME, you just have to log out to some login screen and select your session choice.

---

### Post by Touch.Code on 2007-02-17
Oh yeah, I just noticed that. When your on sessions and select GNOME, it will ask to set as default.

---

