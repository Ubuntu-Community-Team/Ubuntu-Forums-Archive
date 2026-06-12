---
title: "Automatically load and then quit program (nvidia-settings) on startup?"
date: 2007-01-19
forum: General Help
---

### Post by Bastanteroma on 2007-01-19
My nvidia card displays colors a little oddly, but I compensate using the controls in nvidia-settings.  These color corrections aren't in effect when I boot though, so I have to start nvidia-settings and then close it (I don't need to do anything in it, just open and close).

Anyone know how to do this automatically?

Thanks

---

### Post by 454redhawk on 2007-01-19
I use this in the sessions startup tab.


```
nvidia-settings --load-config-only
```

nvidia-settings must have been at least once in order for settings to be restored. The settings file is stored in ~/.nvidia-settings-rc

---

