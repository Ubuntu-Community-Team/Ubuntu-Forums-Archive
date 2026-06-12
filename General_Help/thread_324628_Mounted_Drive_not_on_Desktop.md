---
title: "Mounted Drive not on Desktop"
date: 2006-12-24
forum: General Help
---

### Post by zombie_killer on 2006-12-24
I've got a second hdd which *is* mounted on startup, but there's no icon showing up on my desktop.  How do I fix this?  I'd rather not have to navigate to it in Nautilus every time I want to access it.  Thanks.

Oh, and I tried creating my own custom launcher, but the icon ended up being HUGE, and it still didn't solve my problem of why the icon is being added automatically.

---

### Post by xopher on 2006-12-24
There is a gconf option:

> 
ALT+F2 -> gconf

In gconf:

apps-> nautilus-> desktop

make sure "volume_visible" is checked.

---

### Post by zombie_killer on 2006-12-24
The option was already checked.  I unchecked it, restarted X, then checked it again, and restarted X--nothing.

---

### Post by zombie_killer on 2006-12-24
I got the icon to show up on the desktop--by mounting the drive in /media.  Is there anyway I can get devices in /mount to show up on the desktop?

---

