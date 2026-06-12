---
title: "Start New X Without Root Privileges?"
date: 2007-11-26
forum: General Help
---

### Post by Githlar on 2007-11-26
Is this possible? I created a shell script to start a new X server on display :1 at a low resolution and then start a game that's hard to play at the resolution I use. Well, my problem is, my friend likes to play this game. If I created a launcher to the script, I'd have to enter my password every time. Or tell him my password when he wants to play.. Both alternatives are unacceptable.

I understand that the file /etc/X11/Xwrapper.config can change this, but I don't want just ANYBODY to be able to start the X server. Is there a way that I can manage a specific user list than can run X?

The error I get when starting X:
> X: user not authorized to run the X server, aborting.

---

