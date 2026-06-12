---
title: "(py)QT 5.4 on trusty?"
date: 2015-02-20
forum: General Help
---

### Post by lykwydchykyn on 2015-02-20
I'm running Trusty on my main work machine, and don't really want to upgrade the whole thing at this point; but I need pyqt 5.4 to work on a project.  I've looked for a PPA, but there doesn't seem to be one.  I could try backporting Qt 5.4 to Trusty by compiling the code, but I'm afraid it'd break all my Qt/KDE applications.

Is there any way I can update pyqt and Qt in a sandbox of some sort so that I could work on my project on this machine, but not affect my existing Qt applications?

---

### Post by dragonfly41 on 2015-02-20
A couple of ideas ..

(a) You could create a new user account for QT5 sandbox only.  Perhaps a bit drastic.

OR

(b) Install QT5 and then run commands ...

[INDENT=2]qtchooser -list-versions
EXPORT QT_SELECT <choice of QT version as listed from qtchooser>
[/INDENT]

---

