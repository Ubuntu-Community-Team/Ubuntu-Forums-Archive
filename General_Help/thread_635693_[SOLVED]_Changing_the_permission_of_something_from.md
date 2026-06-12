---
title: "[SOLVED] Changing the permission of something from the command line?"
date: 2007-12-09
forum: General Help
---

### Post by blithen on 2007-12-09
How do I do that?
The permissions of my CDROM0 got changed and everytime I try to access it through GUI it freezes.
Anyone know the code?

---

### Post by Crashmaxx on 2007-12-09
Use chmod and chown, read the man for more details, but in general, to change permissions:
```

sudo chmod [-R for folders] [3 or 4 digit permissions octal, like 755] [path to file or folder]

```
And to change owner and group:
```

sudo chown [-R for folders] [owner]:[group] [path to file or folder]

```

---

### Post by Lostincyberspace on 2007-12-09
login as root and fix it.

---

### Post by blithen on 2007-12-09
> **Lostincyberspace said:**
> login as root and fix it.
sudo gnome-open /media does that >_>

---

### Post by blithen on 2007-12-09
Sweet thanks for the info crashmaxx, everything is okay now!

---

