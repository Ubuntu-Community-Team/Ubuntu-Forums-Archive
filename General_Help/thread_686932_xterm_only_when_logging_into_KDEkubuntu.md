---
title: "xterm only when logging into KDE/kubuntu"
date: 2008-02-03
forum: General Help
---

### Post by B'man on 2008-02-03
I'm loathed to make two topics for two issues, but hey.

I'm running Kubuntu as a result of installing kubuntu-desktop on Ubuntu. When using KDM instead of GDM, upon logging into KDE, only an xterm window appears in the top left corner of the screen. I can start KDE by running *startkde*, but the xterm window remains, and KDE will quit if I close it.

I'd like to use KDM, since GDM is more sluggish, but I'd prefer not to have to put up with the xterm window and having to start it manually. In GDM, KDE starts as expected. Anyone have any suggestions?

Cheers,
Ian

---

### Post by B'man on 2008-02-15
Haven't found anything on this yet. Anyone?

---

### Post by MacAnthony on 2008-02-15
Sounds like when you login, it's starting a failsafe session instead of starting a kde session. You should get the choice of the session type when you log in. I don't recall the name of the menu and I'm not on my kubuntu box right now so I can't check. But try and make sure it's starting a kde session when you login.

---

### Post by B'man on 2008-02-15
Yeah, I'm definitely using KDE instead of failsafe. Both options are starting up with the xterm window, so it looks like KDE on KDM is acting like a failsafe session or something.

---

### Post by MacAnthony on 2008-02-15
Do you have anything in ~/.xsession-errors ?

Possibly there isn't an option for the kde session in your Xsession file??? I think it's in /etc/xdm, but some one who is at a linux box could probably tell you better.

---

### Post by bilge.tutak on 2008-02-15
What happens if you put startkde in the background :)??

```
startkde &
```

---

### Post by B'man on 2008-02-15
Nothing in ~/.xsession-errors. If startkde is started in the background it returns the process but otherwise is identical in behaviour.

---

