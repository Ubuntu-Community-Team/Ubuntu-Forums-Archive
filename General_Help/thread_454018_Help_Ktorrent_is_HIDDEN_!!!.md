---
title: "Help Ktorrent is HIDDEN !!!"
date: 2007-05-25
forum: General Help
---

### Post by dr_fagshah on 2007-05-25
Hello ....

I've been having problems with Ktorrent . The program start's for about one second then it's hidden and I can't bring to front again .

---

### Post by knallkopf on 2007-05-25
I had the same problem, but not anymore since upgrading to 2.1.4. Try upgrading (you have to compile from source, which takes a while but is well worth it).

Other than that, it usually worked on the second try. So kill ktorrent (killall -9 ktorrent), make sure to close all connections it might have been established (everything listed by ps -AF | grep ktorrent) and try it again. Not really much of a solution, but it works ;-)

---

### Post by dr_fagshah on 2007-05-28
Hi ....


I already have the latest version ....

I also tried to remove the program then re installing it but it's still not working .

---

### Post by p|_eX on 2007-11-04
i had the same problem. reinstall didn't help.
but there's a config file in your home folder:
.kde/share/config/ktorrentrc
change :
[WindowStatus Toolbar KMdiTaskBar]
Hidden=false

that worked for me.

---

