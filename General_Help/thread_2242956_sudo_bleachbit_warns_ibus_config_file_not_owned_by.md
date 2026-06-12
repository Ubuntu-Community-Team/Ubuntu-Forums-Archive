---
title: "sudo bleachbit warns ibus config file not owned by root"
date: 2014-09-05
forum: General Help
---

### Post by klundermann on 2014-09-05
[COLOR=#ff0000][/COLOR]When I run [FONT=system]sudo bleachbit[/FONT] , I get the following error message:

[COLOR=#ff0000]IBUS-WARNING **: The owner of /home/dude/.config/ibus/bus is not root!
[/COLOR]
Should I be concerned about this?  The owner of the file is, not surprisingly, me.

---

### Post by jim_deadlock on 2014-09-05
I get the exact same warning when running CopyAgent. I don't think it matters because root will be able to write there if it wants to.

---

### Post by Impavidus on 2014-09-05
Yes, root can write to that file anyway, but it may make files owned by root. That is something you don't want, as the normal user may lose access to it. The warning message is probably caused by bleachbit running as root but using the normal user's environment (I don't use bleachbit or copyagent myself). This is bad and is the reason why gksu was invented, to use instead of sudo.

---

### Post by klundermann on 2014-09-06
Thanks much.  Next question:  why does Bleachbit come with an "as root" option rather than with a "with gksu" options, and why is gksu no longer part of standard Ubuntu?

---

