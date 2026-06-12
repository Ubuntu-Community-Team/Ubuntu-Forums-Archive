---
title: "Monitor does not go to sleep when locking screen"
date: 2022-02-15
forum: General Help
---

### Post by hateregistering on 2022-02-15
I have a HP Zbook running Ubuntu 20.04.3 LTS attached to a HP Thunderbolt Dock 230W. Before I used the dock the screen went to sleep almost immediately after locking the screen. Now it does not seem to sleep at all. How can I make it behave like before I started using the dock?

---

### Post by #&amp;thj^% on 2022-02-15
1st suggestion, update the firmware for the Dock, and also Linux kernel 5.10.16 or later.

---

### Post by MAFoElffen on 2022-02-15
Have you checked your "Settings" to see if your Power settings have been changed by an update?

First do in a terminal:
```

gsettings list-recursively | grep -e 'org\.gnome\.desktop\.session\|org\.gnome\.desktop\.screensaver' | grep -e 'idle-delay\|lock-delay\|lock-enabled'

```
In you are using dconf-editor, go to the below keys, to reset those keys to what you want...
or set manually on the commandline. These are what mine are set to.
```

gsettings set org.gnome.desktop.session idle-delay 300
gsettings set org.gnome.desktop.screensaver lock-delay 0
gsettings set org.gnome.desktop.screensaver lock-enabled true

```

---

