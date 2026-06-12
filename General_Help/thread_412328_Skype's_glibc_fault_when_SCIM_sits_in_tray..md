---
title: "Skype's glibc fault when SCIM sits in tray."
date: 2007-04-17
forum: General Help
---

### Post by ghostie on 2007-04-17
hi,

I wonder have anyone notice that Skype will not lauch with SCIM is launched ahead of time?

Skype returns following error in terminal.

*** glibc detected *** free(): invalid pointer: 0x08a6c7d0 ***
Aborted

This isn't meaningful to me but I discovered that Skype will only launch normally only before SCIM sits in the tray. Now, how do I prevent SCIM from loading before skype after xwindows' login?

I've tried to login with a new user account without SCIM preloaded; Skype works flawlessly.

I recall that I had similar problem in Hoary where, SCIM returns "segmentation fault" whenever Skype is installed. They are both conflicting with each other and I gave up ubuntu until Dapper released.

thanx in advance!

---

### Post by sevencapitalsins on 2007-04-26
Hi,

I have the same problem in Ubuntu Feisty Fawn.

I searched through Skype forums and got this

[http://forum.skype.com/index.php?showtopic=9468&pid=310835&mode=threaded&show=&st=0&#entry310835]("http://forum.skype.com/index.php?showtopic=9468&pid=310835&mode=threaded&show=&st=0&#entry310835")

Apparently on the Ubuntu Forum there's a thread with the solution, anyway I'll post mine here.

1) i did a very simple script named skypelauncher.sh:
*****
#!bin/sh
XMODIFIERS=@im=none QT_IM_MODULE=xim skype
*****

2) I saved it under ~/.Skype/skypelauncher.sh 

3) I made it executable
*****
chmod u+rwx skypelauncher.sh
*****

4) I modified skype's menu entry (gnome or kde, it works flawlessly) so that the COMMAND executed was
*****
sh ~/.Skype/skypelauncher.sh
*****



It works. And i don't need japanese or chinese or strange letters, luckily :)

Bye
Luca

---

