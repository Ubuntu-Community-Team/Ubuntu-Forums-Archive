---
title: "Faking a power save mouse/keyboard wake-up event"
date: 2007-11-24
forum: General Help
---

### Post by ocwo92 on 2007-11-24
I'm using an Ubuntu installation that uses LIRC (i.e., infrared controls), and which has no keyboard or mouse. I've also enabled power-saving features that turn off the display after a few minutes.

Unfortunately, the LIRC activity does not cause the computer to resume from the power-saving mode so that the user can view what happens on the screen, just as if the user had moved the mouse or used the keyboard.

How can I wake the computer from the display power-saving mode without having to physically jiggle the mouse or press a key on the keyboard?

Using irexec or irxevent to send a key press to an application doesn't cause the computer to resume from its power-saving mode; it sends the key press to the application, but doesn't trigger a wake-up signal.

I assume I should use a command akin to "gnome-screensaver-command --poke", but since I'm using power-saving features instead of screensaver features, this won't work.

Anyone?

---

