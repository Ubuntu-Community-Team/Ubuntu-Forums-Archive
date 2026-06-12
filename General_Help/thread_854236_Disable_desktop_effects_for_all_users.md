---
title: "Disable desktop effects for all users"
date: 2008-07-09
forum: General Help
---

### Post by Max-B on 2008-07-09
Hi,
I have a simple question: how can I disable all desktop effects for all users of PC with Ubuntu 8.04?
Ciao,
Max

---

### Post by sayakb on 2008-07-09
Perhaps uninstall compiz.. :)
```
sudo apt-get remove compiz
```

---

### Post by Max-B on 2008-07-11
Unfortunately it does not works. I removed compiz but I still have desktop effect for the new users.
ciao,
Max

---

### Post by sayakb on 2008-07-11
At a terminal:
```
sudo gedit /etc/X11/xorg.conf
```And add this at the end:
```

Section "Extensions"
    Option "Composite" "Disable"
EndSection
```

And restart X to check.

---

### Post by forger on 2008-07-11
You don't need to uninstall it necessarily...
i.e. If you want to disable it from being the default window manager (but still available to be enabled):
```
gconftool-2 -s /desktop/gnome/applications/window_manager/default -t string '/usr/bin/metacity'
```

If you want to disable (i.e. no-one to be able to use it), uninstall the complete package:```

sudo apt-get purge compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins libcompizconfig0
```
(then log out and log in to enable the changes)

---

### Post by Max-B on 2008-07-11
Thanks very much! It works perfectly!
ciao,
Max

---

