---
title: "How to add command to auto startup"
date: 2015-05-16
forum: General Help
---

### Post by Otto-C on 2015-05-16
Dell B130 laptop. Lubuntu 14.04.2.

On startup the screen is almost too dark to read. Have installed
xbacklight and have cli executed xbacklight -set 100.

Can someone provide me with step by step how to add the command
to the auto startup.

tia
otto-c

---

### Post by SeijiSensei on 2015-05-16
Any command you put in /etc/rc.local will be executed at the end of the boot sequence.

---

### Post by Dennis N on 2015-05-17
> **Otto-C said:**
>  Can someone provide me with step by step how to add the command
to the auto startup.

Lubuntu has a nice user dialog to do this:

Menu > Preferences > Default Applications for LXSession

In the window, click 'Autostart' on the left. Then enter your command in the box next to the 'Add' button under 'Manual autostarted applications'. Then click on 'Add'. (Don't click 'Add' until after adding the command).

Your command should run automatically during the next startup!

---

