---
title: "Stop Windows Key from showing activities"
date: 2019-06-05
forum: General Help
---

### Post by rCXer on 2019-06-05
How can I disable the Windows Key Activities shortcut in bionic?

---

### Post by again? on 2019-06-06
If you prefer it to open application overlay, try this extension.
[https://extensions.gnome.org/extension/1198/start-overlay-in-application-view/](https://extensions.gnome.org/extension/1198/start-overlay-in-application-view/)

Not using gnome-shell, but from here ...
[https://superuser.com/questions/484686/disable-default-gnome-shell-super-key-mapping](https://superuser.com/questions/484686/disable-default-gnome-shell-super-key-mapping)
```
gsettings set org.gnome.mutter overlay-key ''
```

To reset to default...
```
gsettings reset org.gnome.mutter overlay-key
```

---

### Post by rCXer on 2019-06-08
Thanks!

---

