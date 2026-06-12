---
title: "Ubuntu wont start."
date: 2007-03-19
forum: General Help
---

### Post by FuZ3 on 2007-03-19
Hey, I need a little help.

After I made the mistake of letting my little brother use an administrator account I tried to log on and about 5 seconds in it freezes. When running in failsafe mode it gives me the message that says gnome-settings-daemon wont start and some themes and stuff wont work then it freezes.

I tried running gnome-settings-daemon in the xterm mode and it says that it can't communicate with dbus_9 and all connections end in "=NULL" and also that it cant open some icons. I tried installing KDE thinking that If gnome-settings-daemon was the problem then that would fix it but It freezes at the same point. I also tried reinstalling dbus with aptitude from the command line and that didn't help either.

Any suggestions?

---

### Post by Thirsteh on 2007-03-19
If you're able to operate the command-line interface, could you do a 'startx' (root not required) and paste the output here? If Gnome/KDE freezes after running the command, you can use CTRL+1/2/3/4 to get back to the command-line, or kill X with CTRL+ALT+BACKSPACE.

update: Silly me. You probably can't paste it. Anything you think is an error will do :)

---

### Post by FuZ3 on 2007-03-20
:???: For some reason when I input "startx" it runs just fine.

Does that tell you anything?

The only thing I can think of is that either dbus isn't starting with the normal login or there is a problem with GDM.

EDIT: Ok, not everything runs fine. Things like automatically mounting something(like an iPod) and other stuff doesn't work.

---

