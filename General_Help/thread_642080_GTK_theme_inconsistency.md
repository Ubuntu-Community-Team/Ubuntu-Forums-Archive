---
title: "GTK theme inconsistency"
date: 2007-12-16
forum: General Help
---

### Post by usien on 2007-12-16
sometimes when i change the gtk theme, apps running with gksude (synaptic, login screen settings, etc) open with some ancient gtk theme, although i do have a gtk theme set on the root account as well. whats the catch?

---

### Post by Juffo-Wup on 2007-12-16
It seems to me that root doesn't have access to your theme.

You could try renaming root's .themes folder  (where users' themes are stored)

```
sudo mv /root/.themes /root/.themesOLD
```

And then link your own .themes there in its place

```
sudo ln -s ~/.themes /root/.themes
```

As said in [this thread]("http://ubuntuforums.org/showthread.php?t=636143&highlight=root+gnome+theme").

---

