---
title: "use alt key as meta key in gnome-terminal?"
date: 2008-03-03
forum: General Help
---

### Post by baltimorecrank on 2008-03-03
In gnome-terminal, I want the alt key to be the meta key. For example, I want to press alt-f to jump to the next word or alt-b to jump to the previous word on the command line. Currently, that is esc-f and esc-b instead. How can I make it work with the alt key instead of the esc key?

Thanks!
--Markus

---

### Post by fedex1993 on 2008-03-03
i think there is some manager you can install to change everything like configuration editor. its hidden under system tools

---

### Post by baltimorecrank on 2008-03-03
> **fedex1993 said:**
> i think there is some manager you can install to change everything like configuration editor. its hidden under system tools

I see System -> Preferences -> Keyboard where it tells me under 'Layout Options' that "Alt and Meta are on the Alt keys", but that doesn't  help with my gnome-terminal problem.

---

### Post by soldats on 2008-03-03
try holding ctrl and right/middle/left clicking the mouse in the terminal and see if a general menu comes up. for me on a left click there is an option for meta as escape, there may even be the option for alt as escape. i think i recall some options in the gnome terminal menu itself.

---

### Post by baltimorecrank on 2008-03-04
> **soldats said:**
> try holding ctrl and right/middle/left clicking the mouse in the terminal and see if a general menu comes up. for me on a left click there is an option for meta as escape, there may even be the option for alt as escape. i think i recall some options in the gnome terminal menu itself.

Hmm, I don't see such an option. A menu comes up when I right-click on the terminal window. There I can do "edit current profile", but there is no setting for the meta key.

---

### Post by baltimorecrank on 2008-03-04
I found that alt+shift works as meta key. Not quite what I wanted, but maybe I can get used to that or the esc key.

---

### Post by kdotsky on 2008-04-08
I had the same problem.  In gnome-terminal, go to Edit -> Keyboard Shortcuts.  Checkmark the box labeled "Disable all menu access keys (such as Alt+f to open File menu)".

---

