---
title: "Can't Drag Windows"
date: 2007-01-02
forum: General Help
---

### Post by Buck2348 on 2007-01-02
I installed Compiz.  Now I can't drag windows, and there are no minimize, maximize or close buttons.  I uninstalled Compiz, no help.  I also reinstalled Nautilus.  Anybody seen this problem before?

Thanks,
Buck

---

### Post by invalid on 2007-01-02
> **Buck2348 said:**
> I installed Compiz.  Now I can't drag windows, and there are no minimize, maximize or close buttons.  I uninstalled Compiz, no help.  I also reinstalled Nautilus.  Anybody seen this problem before?

Thanks,
Buck

Until someone can suggest how to restore your window decorations, you should be able to move windows by holding alt.

---

### Post by cmost on 2007-01-02
Yeah, you haven't loaded the compiz window decorator.  I use Beryl myself and the window decorator component is called emerald.  Compiz uses decorators to draw the window borders with the usual minimize, maximize and close buttons.  Compiz provides two window decorators:  (1.) gtk-window-decorator uses either a basic cairo based rendering engine or can use metacity themes.  (2.) kde-window-decorator uses native KDE themes.  Try opening a terminal and typing (note the dollar sign is the prompt:)

$killall gtk-window-decorator
$gtk-window-decorator &

Post the output you get from this command.  Good luck!

---

### Post by Buck2348 on 2007-01-02
I can't paste either, I just found out.  killall gtk-window-decorator produced:
gtk-window-decorator:  no process killed
gtk-window-decorator produced:
command not found

Thank you for your replies.

Buck

---

### Post by cmost on 2007-01-02
[LEFT][/LEFT"killall gtk-window-decorator produced:
gtk-window-decorator: no process killed
gtk-window-decorator produced:
command not found"

This tells me that you don't have the gtk-window-decorator installed.  Without it, you won't be able have window decorations.  Go back to whichever tutorial you used to install Compiz, or, check out the help section on the compiz site and find out what went wrong.  Then, try to install the decorator.

---

### Post by Buck2348 on 2007-01-03
Thanks again for your replies.  I ended up doing a reinstall of Edgy--much easier than trying to track down that problem.  I had to wipe out my /home directory for even that to work.

Buck

---

