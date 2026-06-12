---
title: "Autostart issues"
date: 2013-11-30
forum: General Help
---

### Post by AussieGuy on 2013-11-30
Recently I installed a full kde onto my ubuntu 12.04 system: I like kde over gnome.  However, for some reason whenever I start up, I get an evince window with an error telling me that the file is unavailable.  I've checked my ~/kde/Autostart and ./kde/share/autostart directories, and they are both empty.  I've also checked out ~/.config/evince.  I'm not quite sure where on the system to find either a script or a file which tells evince to start up automatically.  Also, emacs autostarts, which is fine, but the window is the wrong size, and the autostart directory is wrong.  (I'm not sure whether this is an autostart issue or an emacs issue).  Any ideas how can I sort out what autostarts, and how?

---

### Post by mikewhatever on 2013-11-30
Anything in ~/.config/autostart?

---

### Post by AussieGuy on 2013-11-30
Good call: but ~/.config/autostart contains only files for dropboxd (which does indeed start up), google chrome (which doesn't start up), and a weather indicator.  There must be something which is over-riding this.

---

### Post by mikewhatever on 2013-11-30
OK, why not look for it in the home folder with something like this:
```

find . -type f -name "*gedit*"

```

...if that doesn't help, try something more general like:
```

find . -type -f -name "*.desktop"

```

---

