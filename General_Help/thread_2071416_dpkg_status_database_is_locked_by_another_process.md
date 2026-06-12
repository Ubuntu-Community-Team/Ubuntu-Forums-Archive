---
title: "dpkg status database is locked by another process"
date: 2012-10-15
forum: General Help
---

### Post by denzos on 2012-10-15
I have accidentally removed "libqtcore4".

 So each time i try to install something using apt the following error msg reviles: 

 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

 what to do??

---

### Post by steeldriver on 2012-10-15
That's usually because another package manager (such as Synaptic - or whatever is used in Kubuntu - Adept maybe?) is open - close it and try again

---

### Post by Habitual on 2012-10-15
[http://www.linuxquestions.org/questions/linux-software-2/accidentally-deleted-libqtcore4-how-do-i-recover-4175432288/](http://www.linuxquestions.org/questions/linux-software-2/accidentally-deleted-libqtcore4-how-do-i-recover-4175432288/)

---

