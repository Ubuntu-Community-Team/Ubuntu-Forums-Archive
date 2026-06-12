---
title: "&quot;Quit&quot; freezes my system."
date: 2008-06-02
forum: General Help
---

### Post by mivo on 2008-06-02
I'm not sure when this happened, since I don't reboot my computer normally, but when I select "quit" (either from the system menu or by clicking the quit button in the panel), my box freezes. Mouse still works, but clicks or keystrokes have no effect. I can restart X, and REISUB also works, so it's not a show stopper, but I'd still like to fix this. :) The box with the options (restart, turn off, hibernate, etc.) never shows up. This used to work after I installed Hardy some weeks ago, so it broke at some later point.

Any help is appreciated!

---

### Post by BlueSkyNIS on 2008-06-02
Just be more patient, Quit dialog box will eventually appear after some 30-50 second. You probably switched off "Power Manager" in "Session" window?

---

### Post by Pijits_1 on 2008-06-02
Maybe try a terminal shutdown using ```
sudo shutdown -h now
``` and seeing if it freezes? If it doesn't freeze it could be a gnome error or something.

---

### Post by Pijits_1 on 2008-06-02
Maybe try a terminal shutdown using ```
sudo shutdown -h now
``` and seeing if it freezes. If it doesn't freeze it could be a gnome error or something.

---

### Post by jimv on 2008-06-02
Go to System > Preferences > Session and make sure that Power Manager is checked.

---

### Post by Pijits_1 on 2008-06-02
sorry for the double post, browser was jammed and hit button twice

---

