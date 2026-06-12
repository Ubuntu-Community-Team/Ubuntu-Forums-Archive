---
title: "Is Copy &amp; Paste different in 16.04?"
date: 2017-05-25
forum: General Help
---

### Post by sillyboy on 2017-05-25
Not sure if the copy and paste has changed in Ubuntu 12.04 to Ubuntu 16.04.  The copy and paste in 12.04 worked great, highlight the text, and then press the MMB to paste.

On my install of Ubuntu-Mate 1604, I have to highlight, right click on highlighted text, then choose copy, then left click the field I want to use, right click and choose paste.

This is no different than the way Windows does it.

Is it my installation, or is this the way it is now?  If yes, can this behavior be changed?

Thank You

sb

---

### Post by again? on 2017-05-25
Behaviour hasn't changed here on Ubuntu 16.04 or Ubuntu Gnome 17.04
Gnome tweak tool allows you to to turn off/on middle click paste.
Check the setting **/org/gnome/desktop/interface/gtk-enable-primary-paste** in dconf-editor or
reset to default (true) via terminal.
```
dconf reset /org/gnome/desktop/interface/gtk-enable-primary-paste
```
Don't use Mate so can't give a definitive answer.

P.S primary paste is cleared once you close the application in which you highlighted text.

---

