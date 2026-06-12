---
title: "Ubuntu 13.10 Keybord Shortcut"
date: 2014-01-28
forum: General Help
---

### Post by tecknomage on 2014-01-28
**RIG:** Laptop running Ubuntu 13.10 running _GNOME Flashback desktop_

When I go to [System Settings][Keybord], [Shortcuts] tab, and try to create a **Custom Shortcut**, the dialog wants a command line.

What **command line** would I enter to run **Restart** :confused:

**Example:** [Ctrl][Alt][R] would run **Restart**.

---

### Post by stinkeye on 2014-01-28
```
gnome-session-quit --reboot
```

You will need to confirm.
See **man gnome-session-quit**

---

