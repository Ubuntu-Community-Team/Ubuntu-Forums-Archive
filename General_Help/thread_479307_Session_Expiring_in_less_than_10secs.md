---
title: "Session Expiring in less than 10secs"
date: 2007-06-20
forum: General Help
---

### Post by Nrad^ on 2007-06-20
Everything was fine with my system besides that i tried to install realtek drivers and then after that nothing opened, so i thought Ubuntu crashed!  Restart!  then i get this error:

[COLOR="Orange"]error while loading shared libaries: libasound.so.2: cannot open shared object file: No such file or directory[/COLOR]

WHat i did previously before this crash and boot failure, i tried to install teh realtek drivers via SU just followed the readme that came with it.

---

### Post by Nrad^ on 2007-06-20
Oh forgot to say, Ive tried the terminal failsafe and i have no clue what to do in that and i have tried to use the fail safe GNOME but its keep sessioning out!

---

### Post by ronmarley1 on 2007-06-20
Boot to a failsafe terminal and uninstall what you tried to install.
```
sudo apt-get uninstall "application name or whatever you tried to install"
``` without the quotes.

---

