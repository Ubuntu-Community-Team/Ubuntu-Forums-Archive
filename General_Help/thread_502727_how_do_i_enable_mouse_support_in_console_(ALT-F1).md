---
title: "how do i enable mouse support in console (ALT-F1) ?"
date: 2007-07-17
forum: General Help
---

### Post by kraymore on 2007-07-17
how do i enable mouse support in console (ALT-F1) ?

---

### Post by James Hales on 2007-07-17
You will be wanting a package called "gpm" from Synaptic. I haven't tried this on Ubuntu, but on other distributions there is normally a script that starts it at boot. So if it doesn't work straight away, try restarting your computer. And if that fails, you might want to look under the Service Settings window in GNOME.

*An update:*

I just tried installing it. If you want to start it without restarting, you can use:

```
sudo /etc/init.d/gpm start
```

---

