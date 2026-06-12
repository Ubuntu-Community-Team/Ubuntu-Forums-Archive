---
title: "Wine Menu not displaying"
date: 2007-11-01
forum: General Help
---

### Post by benji.ijneb on 2007-11-01
i installed wine - and then uninstalled it.
unfortunately, i did the stupid thing of deleting the wine menu in the taskbar, and now i can't get it back (now that i've installed it.....again) Help!

---

### Post by Crafty Kisses on 2007-11-01
> **benji.ijneb said:**
> i installed wine - and then uninstalled it.
unfortunately, i did the stupid thing of deleting the wine menu in the taskbar, and now i can't get it back (now that i've installed it.....again) Help!

What version of Ubuntu are you using?

---

### Post by strabes on 2007-11-01
Does the following fix your problem? ```
sudo aptitude purge wine && sudo aptitude install wine
```

---

### Post by Whiffle on 2007-11-01
Or try

rm -fr ~/.wine
wine regedit

and hopefully it will recreate them..

---

### Post by benji.ijneb on 2007-11-02
> **Codename said:**
> What version of Ubuntu are you using?

Gutsy

---

