---
title: "Wierd Errors During Boot..."
date: 2007-11-21
forum: General Help
---

### Post by prodezigner on 2007-11-21
I'm running 7.10 Server Edition... everything works fine, but during boot I get some wierd messages and I'd like to see these messages in a log so I can post them on here and get some advice on how to fix these problems. This is just a temporary server, but I've put in a better video card, more RAM, upped the disk space and drive count, etc.

I'm just picky, but ya know... cleanliness is *close* to Godliness.

---

### Post by Bolorino on 2007-11-21
To search for those boot messages type in a console:
```
dmesg
```

That outputs kernel messages.

Good luck.

Some logs to take a look to:
/var/log/boot
/var/log/messages

---

