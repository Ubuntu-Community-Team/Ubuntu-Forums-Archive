---
title: "shutdown at certain time (shutdow -t +m240)"
date: 2006-11-14
forum: General Help
---

### Post by GnomicGhost on 2006-11-14
Hi all,
I used to know how to shutdown the comp at a certain time instead of right this second but I've forgotten the commands.
shutdown now is:
sudo shutdown -h now
what I want is to shutdown in either at a time, like 06.00am, or +240mins from now.
I've tried things like, and variations of these:
sudo shutdown -t +m240
sudo shutdown -t 06.00
but I can't seem to get it.  The man pages don't seem to help either.

Thank you.

---

### Post by Ziggurat on 2006-11-14
```
sudo shutdown -h +240
```

---

### Post by GnomicGhost on 2006-11-14
ahh lol. Thank you! :)

---

