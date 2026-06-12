---
title: "nxclient does nothing"
date: 2007-04-25
forum: General Help
---

### Post by gekkos on 2007-04-25
Hi,
I am using the NoMachine NX client (1.5.0-114) with windows XP to connect to my freenx server (on Linux). On one XP machine I can connect without any problems using this client but from another XP machine the NoMachine NX client shows message "Setting up the X environment" and nothing else happens. I can connect to the linux installation via ssh no problem. Had someone this kind of problem already and has an idea whats going on??
Many thanks

---

### Post by capitalistpiglet on 2007-04-27
freenx sometimes has problems with new windows nx client try a older 1.4 client

---

### Post by gekkos on 2007-04-30
I found the problem but dont get a solution.
The problem is that rsync service is running which uses cygwin1.dll, When I stop this service the nxclient works fine. Someone an idea to get these both working fine together?
Thanks

---

