---
title: "Stop ctrl,alt+backspace restarting gnome"
date: 2007-03-26
forum: General Help
---

### Post by StevenX on 2007-03-26
I'm having trouble with my computer randomly restarting gnome or Xorg or whatever by (I THINK) involuntarily pressing ctrl+alt+backspace.

It always happens when I'm deleting text from a chat window in Gaim, but I don't really think about what other keys I'm holding down as I'm typing too fast. It seems to be SHIFT that does it, as that's held down if I want to add a capital letter. So if the shift, backspace and space or somethign coincide a little it seems to restart gnome.

Does anyone know why this may be, and if removing the setting to restart Gnome by the backspace related keystroke may fix this?

---

### Post by will_in_wi on 2007-03-26
Open a terminal and type: (yes case matters)
```
sudo nano -w /etc/X11/xorg.conf
```
Then find the ServerFlags section and add a line under it that says:
```
Option "DontZap"  "True"
```
Restart your computer and then ctrl-alt-backspace will no longer kill xorg.

---

### Post by StevenX on 2007-03-27
> **will_in_wi said:**
> Open a terminal and type: (yes case matters)
```
sudo nano -w /etc/X11/xorg.conf
```
Then find the ServerFlags section and add a line under it that says:
```
Option "DontZap"  "True"
```
Restart your computer and then ctrl-alt-backspace will no longer kill xorg.

I don't have that line in my xorg conf file, BUT I've found that that isn't actually the issue after a bit of investigation. The problem is a bug in Beryl to do with keys being mapped wrongly, and causing SHIFT+BACKSPACE to restart xorg. The following link has a solution I used (to map the super key to the win key).
[http://forum.beryl-project.org/viewtopic.php?f=39&t=245&p=1295](http://forum.beryl-project.org/viewtopic.php?f=39&t=245&p=1295)

Thanks for helping :)

---

