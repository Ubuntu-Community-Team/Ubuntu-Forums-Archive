---
title: "Error retrieving accessibility bus address: org.freedesktop.DBus.Error.Spawn.ChildExi"
date: 2015-07-09
forum: General Help
---

### Post by susja on 2015-07-09
Hello,
Not sure that the issue is related Ubuntu :)
I just found similar issue reported on Ubuntu site and it had a header : "packagekit in maverick causes error in apt operations" and decided to ask here.
In my case I am running Windows 7. I installed Cygwin, and with cygwin I installed X11, emacs and python packages. Everything works fine but when I try to start emacs from command line I get this error:
--
[SIZE=1]$ emacs


** (emacs:57184): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.a11y.Bus exited with status 1
--
That Ubuntu Bug states that exact same error was caused by /etc/apt/apt.conf.d/20packagekit and deleting it resolved the issue.
In my case I don't see /etc/apt ..
Could someone clarify what the problem is and should I care or could ignore it since it does not impact my emacs executin because I do 2> /dev/null and don't see the Warning.
Thanks in advance
[/SIZE]

---

