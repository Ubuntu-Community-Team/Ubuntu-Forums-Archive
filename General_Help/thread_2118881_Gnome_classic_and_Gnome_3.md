---
title: "Gnome classic and Gnome 3?"
date: 2013-02-22
forum: General Help
---

### Post by joemartin on 2013-02-22
Hello,  I have Gnome Classic and Gnome 3 installed as my only DE's on 12.10.  Is there a way to delete all of Gnome 3 and run Gnome Classic exclusively? Or, are they dependent on one another?

Thanks.

---

### Post by dino99 on 2013-02-22
note that gnome-classic is only a fallback mode of actual gnome3, and PP is the last release using it. Gnome3 via gnome-shell will be the default and will provide a gnome classic mode (but different from the actual fallback).

as some users have not been happy with gnome3 from the start, some forks have been made to get the gnome2 look & feel for some more times: Lubuntu, UGR, SolusOs, ... but some DE fork too like cinnamon, ....

there are some threads here about gnome2 forks.

so gnome3 cant be removed from the default ubuntu

---

### Post by Frogs Hair on 2013-02-22
The gnome-session-fallback can be installed independently. Remove the Gnome Shell from the software center and run the following command or locate the fall back session in the software center.

```
sudo apt-get install gnome-session-fallback  

```

---

### Post by joemartin on 2013-02-22
Thanks for the reply.

If that's the case can you explain how I would get rid of both Gnome 3 and Gnome Classic?  I believe I will likely go with Mate.  A big fan of Gnome 2.  Cinnamon just does not feel as polished as Mate.

---

### Post by Frogs Hair on 2013-02-22
Removing the Gnome Shell should do the trick because the fallback-session is a dependent package.

---

