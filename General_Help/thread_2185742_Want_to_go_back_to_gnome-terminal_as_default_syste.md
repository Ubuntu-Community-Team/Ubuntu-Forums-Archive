---
title: "Want to go back to gnome-terminal as default system terminal after upgrade to 13.10"
date: 2013-11-04
forum: General Help
---

### Post by theronmuller on 2013-11-04
I've tried vala-terminal for two days now and it doesn't cut the mustard. I would like to set gnome-terminal as the default system terminal but am not sure how to go about doing it. Any advice would be welcome.

---

### Post by CaptainMark on 2013-11-04
If you uninstall vala-terminal then everything will fall back to gnome-terminal

---

### Post by steeldriver on 2013-11-04
It looks like vala-terminal inserts itself as the highest priority alternative for 'x-terminal-emulator' in update-alternatives - you should be able to choose gnome-terminal manually by running

```
$ sudo update-alternatives --config x-terminal-emulator
```

You might want to check the value of 'org.gnome.desktop.default-applications.terminal' in gsettings as well

```
gsettings list-recursively org.gnome.desktop.default-applications.terminal
```

---

### Post by theronmuller on 2013-11-05
Thanks! Uninstalling vala-terminal did the trick.

---

