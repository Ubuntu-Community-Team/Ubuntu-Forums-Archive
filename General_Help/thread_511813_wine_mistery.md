---
title: "wine mistery"
date: 2007-07-28
forum: General Help
---

### Post by vexorian on 2007-07-28
I use a bash script to call wine on warcraft III and make it load a map:

```

#!/bin/bash

cd /media/sdb1/Warcraft\ III/
cp -T "$1" /winedrivec/tmpmaps/tmp.w3x

wine ./war3.exe -opengl -window -loadfile "\"c:\\tmpmaps\\tmp.w3x\""

```

Warcraft III is a game that had this hidden -loadfile command thus users are not supposed to use it, and if -loadfile gets an unexistant file as argument it crashes.

I decided to use /winedrivec instead of home for wine since I don't have much GBs on /home/ but / got plenty of it.

Anyways, the issue right now is that no matter how much correct arguments I give to it the game will always freeze when it begins. Notice that "\"c:\\tmpmaps\\tmp.w3x\"" is constant and I know that /winedrivec/tmpmaps/tmp.w3x is created correctly.

What makes this weird is that if I use winedbg instead of wine, and then just do an step, everything will work correctly and the map is loaded.

Isn't it weird that winedbg detects the file correctly and wine doesn't? Should I file a bug about this in wine's bugzilla?

(PS: when I use warcraft III on wine without -loadfile, all goes all right)

---

