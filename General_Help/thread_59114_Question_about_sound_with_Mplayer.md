---
title: "Question about sound with Mplayer"
date: 2005-08-22
forum: General Help
---

### Post by egnaro on 2005-08-22
I have the newest version of mplayer installed. I complied everything myself. The issue it running into it this. If I go to system/preferances/sound and have a check in "enable sound server startup" I get not sound in mplayer. If I uncheck that, i get sound in mplayer, but then of course I get no system sounds, and my gaim has no sounds. Is there a way to make them both work, or do I have to decide between one or the other?

[[IMG]http://img365.imageshack.us/img365/1381/mplayer9gf.jpg[/IMG]](http://imageshack.us)

---

### Post by jasmuz on 2005-08-22
Gnome uses ESD for sound output, you should change the preference of sound in Mplayer to ESD or ALSA to see wich works the best for you.

---

### Post by egnaro on 2005-08-23
Thanks alot! I had to recompile with ESD support, and now all works fine. Thanks again!

---

