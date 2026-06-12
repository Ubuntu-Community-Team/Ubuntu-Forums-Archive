---
title: "cant update or install programs"
date: 2016-12-04
forum: General Help
---

### Post by alfonsnp on 2016-12-04
So i'm running a ubuntu server an a VM and every time i try to update ect I get

 lock /var/lib/dpkg/lock - open (11: resource temorarily unavailable   
 unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by oldos2er on 2016-12-04
You have more than one package manager front-end, such as Software Center, Update Manager, or something else open at once (although the GUI programs are not installed by default in Ubuntu Server). Close them all and try updating again. Or try ```
ps -A | grep apt-get
``` or ```
ps -aux | grep 'apt-get'
``` to find those processes, then kill them and retry updating.

---

### Post by alfonsnp on 2016-12-04
thx I'll give it a shot in a bit..... worked

---

