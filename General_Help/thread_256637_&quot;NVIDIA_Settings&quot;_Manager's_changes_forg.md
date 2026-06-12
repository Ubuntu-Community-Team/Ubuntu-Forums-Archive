---
title: "&quot;NVIDIA Settings&quot; Manager's changes forgotten upon startup"
date: 2006-09-13
forum: General Help
---

### Post by Psycs on 2006-09-13
I installed the Nvidia Drivers with Automatix, 

They allow me to use the "NVIDIA Settings" manager installed under the "System Tools" menu to adjust the brightness, contrast and gamma on my laptop's screen.

However, every time I restart the computer, the Manager has to be opened and closed for the settings to be re-applied.

Is there any way to have these changes load automatically upon startup?

Thanks for the help!

---

### Post by fotakis on 2006-11-08
Did you ever find a solution to this problem?

> **Psycs said:**
> I installed the Nvidia Drivers with Automatix, 

They allow me to use the "NVIDIA Settings" manager installed under the "System Tools" menu to adjust the brightness, contrast and gamma on my laptop's screen.

However, every time I restart the computer, the Manager has to be opened and closed for the settings to be re-applied.

Is there any way to have these changes load automatically upon startup?

Thanks for the help!

---

### Post by 454redhawk on 2006-12-16
Goto System-->Preferences--> Sessions-->Startup Programs. And add

```
nvidia-settings --load-config-only
```

nvidia-settings must have been at least once in order for settings to be restoed.

---

### Post by galileon on 2007-01-29
cheers, that works

---

