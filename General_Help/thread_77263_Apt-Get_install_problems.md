---
title: "Apt-Get install problems"
date: 2005-10-16
forum: General Help
---

### Post by bmbeeman on 2005-10-16
I did an apt-get install xboard and it installed everything fine, but I can't find the program under any of the menus and when I choose "run application" and type xboard it says the directory does not exist, any ideas?

---

### Post by Hikaru79 on 2005-10-16
For some reason, some games directories are not in the path by default. Check /usr/games and /usr/local/games for xboard. It should be there.

---

### Post by az on 2005-10-16
[QUOTE=bmbeeman]I did an apt-get install xboard and it installed everything fine, but I can't find the program under any of the menus and when I choose "run application" and type xboard it says the directory does not exist, any ideas?[/QUOTE]
Look at the list of files in the package.  Use synaptic or packages.ubuntu.com

usr/games/cmail						    games/xboard [universe]
usr/games/pxboard					    games/xboard [universe]
usr/games/zic2xpm					    games/xboard [universe]

---

