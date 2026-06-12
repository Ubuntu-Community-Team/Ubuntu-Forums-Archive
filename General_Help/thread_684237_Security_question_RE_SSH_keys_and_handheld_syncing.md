---
title: "Security question RE: SSH keys and handheld syncing"
date: 2008-01-31
forum: General Help
---

### Post by jaem on 2008-01-31
Hey all,

Here's the situation:
I have a Palm handheld running Angstrom Linux, with the handheld version of KDEPIM on it.  I want to sync it with my laptop, running Ubuntu, over scp.  Now, the setup requires that the handheld initiate the secure session, so, as per [this tutorial]("http://osdir.com/ml/kde.users.pim/2005-05/msg00135.html") I've had to put my private key on the handheld.  Then I sat back and thought about what a bad idea that was... seeing as a handheld is very easily stolen or lost, I don't like the idea of giving anyone who gets their hands on it even non-root access.
I had thought about creating a dummy user with no rights, and moving ~/.kde/share/apps/ to it's home directory - then symlinking it back into mine.  I don't imagine this would work well, however.  What I'm looking for is a way to use the original setup, but give the handheld only access to my PIM data (calendars, contacts, etc.) stored in ~/.kde/share/apps/, so I don't have to worry about security issues (as much).  Alternatively, if there is a better way, please tell me.  Two things to keep in mind are that I need it to be by key only, so it can be easily automated, and that the handheld automatically logs in as local root; there is no password on the handheld.

Thanks,
Jeff

---

### Post by jaem on 2008-01-31
sorry, that was a stupid question :P  I figured it out on my own.

---

