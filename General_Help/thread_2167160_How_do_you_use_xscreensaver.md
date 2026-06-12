---
title: "How do you use xscreensaver"
date: 2013-08-12
forum: General Help
---

### Post by jacatone on 2013-08-12
Xscreensaver doesn't make any sense to me. How do you set it to run a screensaver when the machine is idle after 20 minutes? Thanks.

---

### Post by SweetAurora on 2013-08-12
What Ubuntu version are you using?

---

### Post by jacatone on 2013-08-12
12.04. Gnome-screensaver is better. Will it work on this version of Ubuntu and how do I remove xscreensaver?

---

### Post by Dave_L on 2013-08-12
If you're still interested in using xscreensaver:

Change shortcut Ctrl+Alt+L to use xscreensaver instead of gnome-screensaver:
sudo ln -s /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command

To configure xscreensaver, run from Dash, or run command:
xscreensaver-demo

---

