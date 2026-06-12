---
title: "KDE: Startup script doesn't run (ALSA)"
date: 2006-12-18
forum: General Help
---

### Post by chucknorris on 2006-12-18
Hello, I have a script to set alsamixer PCM volume to a given level.

It's called alsa-pcm.bash and contains:

#!/bin/bash
/usr/bin/amixer -q set PCM 10% unmute

/usr/bin/amixer -q set PCM 90% unmute &

It's set as executable, and is saved to .kde/Autostart. But somehow the levels in alsa are all at 100% at bootup. If i click the script it sets the levels correctly. 

Any ideas please? Thanks

---

### Post by superbrose on 2007-12-22
It's a bit late to tell you now, but I hope it helps someone out there:

You can run startup scripts by putting them into the [FONT="Courier New"]**~/.kde/env**[/FONT] directory.

---

