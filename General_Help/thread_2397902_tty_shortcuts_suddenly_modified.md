---
title: "tty shortcuts suddenly modified"
date: 2018-08-04
forum: General Help
---

### Post by dkdk on 2018-08-04
Hello,

I am on 18.04 and I am used to press Ctrl+Alt+Fx shortcuts to open a tty console. However, since a few days, I'm getting a strange behavior whenever I press the Alt key:

Alt+PrintScreen now opens tty5, which makes screenshots hard to do
Alt+RightArrow opens tty3, LeftArrow opens gdm login screen, which interferes with Firefox navigation shortcuts

Also I noted that I don't need to press Ctrl anymore to open a tty with Alt+Fx

I am wondering what happened. I've been looking in the Gnome settings to find if keyboard shortcuts where changed, but it looks like it's not Gnome that handles tty switch from keyboard.

What could be the root cause ? How can I revert to saner shortcuts ? Is this something that was pushed from the latest 18.04 update?

---

### Post by dkdk on 2018-08-04
Rebooting fixed the problem. I'll see if it happens again.

---

