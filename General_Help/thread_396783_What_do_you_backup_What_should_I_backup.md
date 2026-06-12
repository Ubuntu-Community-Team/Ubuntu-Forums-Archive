---
title: "What do you backup? What should I backup?"
date: 2007-03-29
forum: General Help
---

### Post by ndefontenay on 2007-03-29
Hi,

I'm considering getting a little more advanced... and risky with ubuntu.

Bottom line is never get risky without backups. So what should I put on CD to be able in the worst case, to re install ubuntu and re-configure with minimum pain?

I'm thinking about:

1) /etc/apt/sources.list
2) /etc/X11/xconfig

Should I have my environment variablest too?

What else?

What would you backup?
I've been digging around but haven't seen a good thread on that yet.

Nico

---

### Post by zorkerz on 2007-03-29
All i ever back up is my home directory and my music directory. I have never backed up any config files though i dare say it is probably not a bad idea.

---

### Post by yabbadabbadont on 2007-03-29
Save yourself some pain, tar up the entire /etc directory tree.  It isn't very large and that way you have it if you need it later.  Also backup all of /home.  (always a good idea)  If you have /home on a seperate parition, that will make things easier too.

---

