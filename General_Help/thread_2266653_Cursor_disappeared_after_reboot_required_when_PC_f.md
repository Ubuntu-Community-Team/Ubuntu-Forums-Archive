---
title: "Cursor disappeared after reboot required when PC froze"
date: 2015-02-24
forum: General Help
---

### Post by Jonners59 on 2015-02-24
My PC froze and I was forced to hit the rest button.  When the PC rebooted my courser was not visible.  It was there but not to the eye.  I fixed it with:
Open up a terminal, then typed.

```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```

It immediately appeared.

Hope this helps someone else.

---

