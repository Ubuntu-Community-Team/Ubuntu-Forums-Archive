---
title: "tightvncserver Clipboard sharing"
date: 2008-04-24
forum: General Help
---

### Post by speaker219 on 2008-04-24
I'm using tightvncserver on my linux computer to share the desktop, and i've been noticing that the clipboard *does* share with stuff that is copied on the linux machine, but if i copy something on the windows machine and try to paste it into the linux machine via vnc, it does not work. Tried with about 3 vnc clients on windows, none of which work. Any help would be appreciated
EDIT: The clipboard sharing does not work either way

---

### Post by speaker219 on 2008-04-24
EDIT #2: If i use xcutsel i can copy stuff from linux, but i still can't do it from windows to linux. Thanks!

---

### Post by anttir on 2011-04-14
autocutsel -s PRIMARY -fork

seems to work with 64 karmic and ultravnc-XP.

origin: [http://thomas.patrickdepinguin.com/knowledgebase/tight-vnc](http://thomas.patrickdepinguin.com/knowledgebase/tight-vnc)

---

