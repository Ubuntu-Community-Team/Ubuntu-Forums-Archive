---
title: "[SOLVED] sudo issues since install last night ..."
date: 2007-10-13
forum: General Help
---

### Post by Gaki on 2007-10-13
Hello all,

I installed Kubuntu last night and for the first few bootups while I was trying to fix my networking issue with a Realtek card, sudo worked fine and I could obtain root priviledges whenever I needed to.

As of today, though, I went to add some packages and found that I couldn't get into adept or into the advanced properties in the system configuration area (was checking my video driver).  I dropped to the command line and checked to see if I could sudo via the CLI ... password incorrect.  Hmmm.  I tried several cracks at it and got nothing.

I logged back in through recovery mode, ostensibly as root, and checked my /etc/groups and /etc/sudoers files to see if they were fine ... and they were.  The sole user (me) is listed as being admin in the former and the admin group is listed as having sudo priviledges in the latter.  I'm at a loss.  I can't even create a new user with admin priviledges at this point.  Am I stuck manually creating a user via the CLI?

Gaki

---

### Post by Gaki on 2007-10-14
Fixed myself ... never mind.

---

