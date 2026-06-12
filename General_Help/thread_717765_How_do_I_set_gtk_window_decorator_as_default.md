---
title: "How do I set gtk window decorator as default?"
date: 2008-03-07
forum: General Help
---

### Post by Redrazor39 on 2008-03-07
it always defaults to emerald at startup, but I have a theme I like for gtk. How do I make gtk the default at login?

I'd rather not uninstall emerald

every time I start up I always do the routine [Alt]+[F2] and type gtk-window-decorator --replace and that does it, but when I log in again it's back to emerald. How do I default it?

---

### Post by x1a4 on 2008-03-07
Hi,

Add **gtk-window-decorator --replace** to your list of auto-started applications.

---

### Post by chunchengch on 2008-03-07
I got the same problem when I upgraded compiz from 0.6.0 (Gutsy default) to 0.7.1, then I looked into the new script /usr/bin/compiz and found it was not flawless on detecting video drivers and window decorators as the old one did, so I just replaced it with the old one (Gutsy default) and the problem was solved.

Here is the script  [ATTACH]61932[/ATTACH]  (Gutsy default), if you need it. 

After downloading the script, rename it and move it to /usr/bin/

$ mv compiz-0.6.0.sh compiz
$ sudo mv /usr/bin/compiz /usr/bin/compiz-old
$ sudo mv compiz /usr/bin

---

