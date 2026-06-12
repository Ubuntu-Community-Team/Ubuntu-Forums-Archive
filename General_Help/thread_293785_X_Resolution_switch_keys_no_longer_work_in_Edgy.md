---
title: "X Resolution switch keys no longer work in Edgy"
date: 2006-11-05
forum: General Help
---

### Post by ifireball on 2006-11-05
The quick resolution change special-key-combinations, e.g. Ctrl+Alt+Keypad-Plus and Ctrl+Alt+Keypad-Minus seem to have stopped working since I upgraded to Edgy, this is despite the fact that multiple resolution are properly configured in xorg.conf, in fact, running xvidtune -next can still switch the resolution just fine.

Looking more into this, it seems that X still treats this combinations as special, e.g. they do not generate events on "xev" which means they are captured by X and not propagated to the user processes.

I suspected the commercial Nvidia driver for causing this but this seems to occur with the free "nv" driver as well.

Did anybody else encounter this problem? I'm considering posting this as a bug report on Launchpad.

---

### Post by ifireball on 2006-11-08
Bug report in launchpad (and possible hope for solution):
[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/70546]("http://https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/70546")

---

