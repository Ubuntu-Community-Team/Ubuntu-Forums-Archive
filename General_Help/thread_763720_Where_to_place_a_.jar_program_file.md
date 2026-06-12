---
title: "Where to place a .jar program file?"
date: 2008-04-23
forum: General Help
---

### Post by slink on 2008-04-23
I just downloaded a jar file ( [http://lifehacker.com/381057/bananasplit-divides-avi-videos-for-easy-sharing](http://lifehacker.com/381057/bananasplit-divides-avi-videos-for-easy-sharing) ) and I wonder which is the best place to store it for user-wide use. Maybe [FONT="Fixedsys"]/usr/bin[/FONT] ?

Thanks

---

### Post by txcrackers on 2008-04-24
The "standard" BSD/Linux convention is to put "other" programs in /usr/local/bin. However, for applications packaged as JAR files, they only need to be in any directory that is directly readable by all the users on the system that you want access to the application (since you're actually running Java to execute it).

---

### Post by slink on 2008-04-24
I thought /usr/local/bin was for executables compiled by the user but your answer makes much sense. 

Thank you!

---

