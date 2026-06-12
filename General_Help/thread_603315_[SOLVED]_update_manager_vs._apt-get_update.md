---
title: "[SOLVED] update manager vs. apt-get update"
date: 2007-11-05
forum: General Help
---

### Post by johnn1949 on 2007-11-05
Is there any difference between the programs updated when you run the update manager>check for updates,or when you run the sudo apt-get update, sudo apt-get upgrade?

Thanks
john

---

### Post by zvacet on 2007-11-05
No,there is no difference,because all programs are updated from same repsositories.It is just two ways to do things.

---

### Post by Sef on 2007-11-05
Just a different way of doing the same thing.

---

### Post by johnn1949 on 2007-11-05
Thankyou

---

### Post by Roti on 2008-05-15
Hi!

 When I use the update manager, it says that there are 4 updates. I Could even install them.

But when I use apt-get upgrade after apt-get update, I got this

root@roti:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openvpn ssl-cert
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@roti:~#

I think, there are differences. Aren't there?


Roti

---

