---
title: "Unabel to upgrade using apt-get"
date: 2004-11-03
forum: General Help
---

### Post by Dennis_k on 2004-11-03
i hav installed Ubuntu and now i want to upgrade an install some software using apt-get.

When use (e.g.) sudo apt-get install nvidia-glx there is no search on the internet.
using sudo apt-get upgrade, i get the message that there are no updates. I didnt use the function to update during the installation.

PLease help.......

---

### Post by Vulc on 2004-11-03
[QUOTE=Dennis_k]i hav installed Ubuntu and now i want to upgrade an install some software using apt-get.

When use (e.g.) sudo apt-get install nvidia-glx there is no search on the internet.
using sudo apt-get upgrade, i get the message that there are no updates. I didnt use the function to update during the installation.

PLease help.......[/QUOTE]
 did you set the sources list? if not type sudo pico /etc/apt/sources.list

a few lines down you need to remove the # in front of the links, the documentation in sources.list should mention it, uncomment those by removing the #, save it and try upgrading then

---

### Post by Dennis_k on 2004-11-04
Thanks! it works now!  =D>  =D>

---

