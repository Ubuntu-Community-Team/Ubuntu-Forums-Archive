---
title: "irssi dcc"
date: 2006-11-24
forum: General Help
---

### Post by justin on 2006-11-24
I am trying to match the mIRC command /dccserver +s 59 in irssi. It seems the command /dcc server +s 59 should be what I want, but when I try it, it responds "Permission Denied". Any suggestions?

---

### Post by skymt on 2006-11-24
I found [a post](http://dragoncat.net/lists/irssi-users/2002-07/0018.html) on this problem. Listening on port 59 requires root privileges. Running irssi with sudo would work, but it would be very bad security. Your best bet is to try to run on a port higher than 1024 (the lowest non-privileged port).

---

### Post by Lucifiel on 2007-04-28
Ah, I've got the same problem too. Many irc sends use port 59 and nothing else. >>;;

I wonder if anyone knows how to resolve this issue for telling the users to open only 1024 and above, is kinda useless. At the worst, I'll pick terrible security over not being able to use an application.

---

