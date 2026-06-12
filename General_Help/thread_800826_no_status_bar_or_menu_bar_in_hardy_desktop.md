---
title: "no status bar or menu bar in hardy desktop"
date: 2008-05-20
forum: General Help
---

### Post by richardy on 2008-05-20
Hi,
A recent installation of Xubuntu hardy heron on an Asus laptop has started booting with no program status bar or main menu bar on the desktop. Also the screensaver which previously didnt work is now working.

Any ideas?

Cheers.

---

### Post by morgengenuss on 2008-05-20
what kind of asus laptop?
and: press alt+f2 and run the command "xfce4-panel" to see whether that brings back what you call the "main menu bar".

tbh i have not the slightest clue what you mean with "program status bar"...

---

### Post by richardy on 2008-05-21
> **morgengenuss said:**
> what kind of asus laptop?
and: press alt+f2 and run the command "xfce4-panel" to see whether that brings back what you call the "main menu bar".

tbh i have not the slightest clue what you mean with "program status bar"...

Hi, and thanks for replying, your a star, the "xfce4-panel" command did the trick although it doesn't explain why the panels disappeared in the first place. And yes i am not sure what i was thinking about when i called the panels the main menu bar and program status bar. The other minor mystery is why the screen saver (which previously wouldn't work) started working when the panels disappeared. The Asus laptop is a Z9100L and Xubuntu has never completely worked correctly on it.

Any ideas?

Thanks again.

Cheers.

---

### Post by morgengenuss on 2008-05-21
n.p. the panel crashes very rarely, but it still happens. i wouldn't give it a thought (there are millions of reasons why this might happen). in the end you can always bring it back with the command.

regarding your screensaver: could you have a look in synaptic, search for "screensaver" and tell me whether "xscreensaver" or "gnome-screensaver" is installed?
furthermore: you said it didn't work before the panels disppeared, does that mean it works now even though the panels are back?

---

### Post by richardy on 2008-05-21
> **morgengenuss said:**
> regarding your screensaver: could you have a look in synaptic, search for "screensaver" and tell me whether "xscreensaver" or "gnome-screensaver" is installed?
furthermore: you said it didn't work before the panels disppeared, does that mean it works now even though the panels are back?

Hi, screensaver has gone back to not working.

Gnome screensaver is installed but xscreensaver isnt. However xscreensaver-data and xscreensaver-gl are installed.

Cheers.

---

### Post by morgengenuss on 2008-05-23
what happens if you preview a screensaver with gnome-screensaver? does that work?

one option is definitely to use xscreensaver (which was standard in xubuntu some time ago, i think 6.10), i personally use it and would recommend it.

---

