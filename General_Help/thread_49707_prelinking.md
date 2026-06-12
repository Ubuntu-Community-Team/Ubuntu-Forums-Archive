---
title: "prelinking"
date: 2005-07-17
forum: General Help
---

### Post by lee_connell on 2005-07-17
im not positive but i believe after prelinking my system it randomly locks up.  i just recently installed the 686 kernel from 386 and reprelinked.  

Is there a way to un prelink and bring it back to default install?

by installing the 686 kernel and prelinking again, is that even needed?

---

### Post by damonw5 on 2005-07-17
[QUOTE=lee_connell]im not positive but i believe after prelinking my system it randomly locks up.  i just recently installed the 686 kernel from 386 and reprelinked.  

Is there a way to un prelink and bring it back to default install?

by installing the 686 kernel and prelinking again, is that even needed?[/QUOTE]
 I don't know much about prelinking, but... In Synaptic can't you just uninstall the package "prelink"?

---

### Post by lee_connell on 2005-07-17
hey thanks for the reply, i dont know if just uninstalling will do the trick because it's already done it's job and prelinked everything.

---

### Post by SGC on 2005-07-17
Open this file:
/etc/default/prelink

search for this line and change "yes" to "no"
PRELINKING=yes

Then run the prelink:
sudo /etc/cron.daily/prelink

After that you can remove prelink by:
sudo apt-get remove prelink

---

