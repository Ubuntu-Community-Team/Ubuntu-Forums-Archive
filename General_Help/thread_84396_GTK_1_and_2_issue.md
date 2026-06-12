---
title: "GTK 1 and 2 issue"
date: 2005-10-31
forum: General Help
---

### Post by Antioch on 2005-10-31
Is there a way to get GTK1 themes and GTK2 themes working at the same time?

For example, synaptic never themes when I use my GTK2 themes, so I get a nice metacity border and ugly standard GTK innards. I believe it should be possible. XFCE themes both GTK2 and GTK1 applications and they look the same.

Any help?

Thanks!

---

### Post by 23meg on 2005-10-31
The Synaptic issue isn't a GTK1/2 one. It happens because you use Synaptic as root, and it uses root's selected theme to decorate it. Launching gnome-theme-manager as root and selecting your user theme as the root theme will fix it.

---

