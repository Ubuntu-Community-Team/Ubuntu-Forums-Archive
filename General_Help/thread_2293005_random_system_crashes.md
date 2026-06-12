---
title: "random system crashes"
date: 2015-09-01
forum: General Help
---

### Post by Unguidedone on 2015-09-01
I have somewhat new computer, and every other day the computers screen turns a dark blue.  I still hear audio of what ever is playing at time of crash until i power down the computer.  Where can i access the crash logs or find out if this is a hardware or software issue?

im using 14.04 lts 32 bit

---

### Post by tgalati4 on 2015-09-01
If music keeps playing, then perhaps it is just the graphics that are freezing.  Hit Control-Alt-F1 during the next freeze.  You should get a text console where you can login and issue a shutdown:

```
sudo shutdown -h now
```

The log files are in /var/log.  Also check ~/.xsession-errors.  It is a hidden file, so use Control-H to see the hidden files in Nautilus.

```
more ~/.xsession-errors
```

Spacebar to page forward, "q" to quit.

---

