---
title: "erro when doing update"
date: 2007-09-13
forum: General Help
---

### Post by kystorms on 2007-09-13
while trying to "fix" a compiz tut i was trying to follow
I took everything off I could find with compiz, and when i tried to update in terminal

i get this...
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
lisac@lisac-desktop:~$ 

please help, so i can reclaim my desktop

thanks
:(

---

### Post by prince_niceguy on 2007-09-13
search if some other process is runing using update ... run the following commands in terminal and post the results.

ps -aef|grep apt-get

ps -aef|grep aptitude

ps -aef|grep update

---

### Post by kystorms on 2007-09-13
i removed the repo for compiz that i loaded earlier, and redid in synaptic, and it fixed the error for now.... thank  you for the help

:-)
:):):):)

---

