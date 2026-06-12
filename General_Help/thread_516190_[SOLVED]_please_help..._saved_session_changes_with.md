---
title: "[SOLVED] please help... saved session changes with beryl enable... now windos boder n"
date: 2007-08-02
forum: General Help
---

### Post by cyneuron on 2007-08-02
hello there

i started compiz by tying compiz --replace in terminal.

everyting worked fine. but o loggd out with this. in my session settings, save session changes was enables.

so now compiz starts up at everytime i logon, and that too without windows border.

is there any way i can undo the session changes.

have tried logging in gnome failsafe session, starts ok in this.

but when i login again into normal mode, same problem....

please help

---

### Post by ThrobbingBrain66 on 2007-08-02
Open a terminal and type metacity --replace.  This should get your window borders back.

---

### Post by zero-9376 on 2007-08-02
if you cant open a terminal in the GUI session switch to a console and type

DISPLAY=:0.0 metacity --replace &

If your using an ati card and xgl it may be DISPLAY=:1.0

---

### Post by cyneuron on 2007-08-03
solved it

by typing metacity --replace in terminal and then saving changes

---

