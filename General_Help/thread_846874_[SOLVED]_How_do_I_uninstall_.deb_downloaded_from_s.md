---
title: "[SOLVED] How do I uninstall .deb downloaded from sites?"
date: 2008-07-01
forum: General Help
---

### Post by WeEatVista on 2008-07-01
Let's say I downloaded Opera9.50.etch-qt3_i386.deb via the site and installed it using package installer. How would I go about completely removing Opera from my machine?

Thanks in Advance,

We Eat Vista

---

### Post by soccerboy on 2008-07-01
it should show up in synaptic package manager under System>Administration>Synaptic Package Manager.  You can remove it from there.

---

### Post by iaculallad on 2008-07-01
> **WeEatVista said:**
> Let's say I downloaded Opera9.50.etch-qt3_i386.deb via the site and installed it using package installer. How would I go about completely removing Opera from my machine?

Thanks in Advance,

We Eat Vista

On your terminal:

```
sudo dpkg -r package_name
```

---

### Post by WeEatVista on 2008-07-01
I couldn't find it in synaptic, but doing dpkg -r worked!

Thanks for the replies!

---

### Post by ramjet_1953 on 2008-07-02
If you right-click on the .deb package in Nautilus File Manager, it will drop down a menu.
One of the items on that menu is to install with the debi package manager.

Regards,
Roger :cool:

Whoops!

I misread the original title of the thread and thought that WeEatVista wanted to install.

---

