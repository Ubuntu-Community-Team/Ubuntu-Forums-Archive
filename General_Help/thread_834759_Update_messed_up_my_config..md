---
title: "Update messed up my config."
date: 2008-06-19
forum: General Help
---

### Post by Ocxic on 2008-06-19
I just ran a software update, and now my computer looks like this (see attachment)

I have no idea what has happened, or how to go about fixing it, seems gnome didn't agree with the update. my backround image is gone, text and screen size is totally messed up, and when i quit from the system menue it logs me out, not dialog box. what happend?!?!?

---

### Post by iaculallad on 2008-06-19
Try opening your terminal and restore the gnome default:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel

```

---

### Post by Ocxic on 2008-06-19
that did not help still looks the same.  by they my screen res is set at 2048x1536 and that isnot how my screen looks, not to mention that I can't seem to change the resolution either.

---

### Post by iaculallad on 2008-06-19
Try:

```
sudo debconf gnome-panel
```

Or just reset GNOME settings to default. Press Ctrl+Alt+F1 to enter your terminal:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Then press Ctrl+Alt+F7 again to log back in your GUI.

---

### Post by Ocxic on 2008-06-19
that did not help either, I've noticed that i cannot change my background either.

---

