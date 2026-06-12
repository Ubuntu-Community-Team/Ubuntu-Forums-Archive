---
title: "cannot log in"
date: 2012-11-14
forum: General Help
---

### Post by Kevin Jones on 2012-11-14
Dear All,
I am using kubuntu 12.04.

At the splash screen I type username and login password.
After a second or two to think about things the login screen returns, empty...doing the username and password again restarts the cycle.
If I drop to 'console login' I am given the TTY 1 screen...I login with my name, and I am asked for password, I give both and everything works fine.

How can I get to a graphical environment?

Thanks in advance for any suggestions
Kevin Jones

---

### Post by steeldriver on 2012-11-14
It sounds like your X session is unable to start for some reason - sometimes this is because the filesystem is full, or the home dir is unwritable, or your .Xauthority (or .ICEauthority) has become root owned

---

### Post by Kevin Jones on 2012-11-15
steeldriver,

I have no idea why but...deleted a few files, old movies, and I was able to log in under 'failsafe kubuntu' or something like that.
Everything is working really well.

Thanks for the quick help
Kevin

---

