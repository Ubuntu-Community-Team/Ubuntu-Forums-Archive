---
title: "usplash causes problems for X"
date: 2006-09-11
forum: General Help
---

### Post by BerkeleyDude on 2006-09-11
*(Sorry for posting this again - it seems like "Desktop" wasn't the right place)*

Whenever I log out of KDE (without shutting down the computer), the KDM screen is completely messed up: none of it is displayed, except for text boxes. Keyboard doesn't work at all - even the Ctrl-Alt-F# keys.
 
I noticed that I have these programs running:
 
3380 ? Ss 0:00 /bin/sh /etc/init.d/rc 2
4115 ? S 0:00 \_ /bin/sh /etc/rc2.d/S98usplash start
4254 ? S 0:00 \_ chvt 1
 
What is "chvt 1" doing there? Why did it ever need to switch to VT1, and why didn't it succeed?
 
If I manually switch to VT1 before logging out, then those programs disappear. After that, logging out works fine.
 
Any idea what this is about? How do other people deal with this?

---

