---
title: "How to run a program at startup?"
date: 2006-08-03
forum: General Help
---

### Post by diamond on 2006-08-03
I am running the lovely little [wallpapoz]("http://wallpapoz.sourceforge.net/") utility, and I would like to have the wallpapoz daemon start automatically at boot. It's a single file, daemon_wallpapoz.py. I assume that I have to do something with the startup scripts in /etc/init.d (or /etc/rc5.d), but I don't know what. Can somebody help me out?

---

### Post by mlind on 2006-08-03
Ubuntu doesn't really use runlevel5, just 1 and 2.

You can add that script to execute on X login using **Preferences > Sessions** or to execute on certain runlevel using **update-rc.d** (script).

---

### Post by hasimir44 on 2006-08-03
so only levels 1 and 2 ?? wow. i'm at work and can't verify this.. am i correct in assuming level 1 is w/out gui while level 2 is with gui? 

this is interesting. i wonder why it isn't more standard..

---

