---
title: "error in backuppc"
date: 2007-09-07
forum: General Help
---

### Post by varunanohar on 2007-09-07
hi guys

I'm following  [http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc) for installing backuppc.
But i'm facing some problem like 
/var/lib/dpkg/info/backuppc.postinst: line 45: /usr/share/wwwconfig-common/apache-include_all.sh: No such file or directory
 these come when i use the command 
sudo dpkg-reconfigure backuppc.

plz help me to come out of it.

waiting 4 the reply .

Varuna Nohar

---

### Post by mocoloco on 2007-09-07
You don't need to do that, backuppc is in the repositories.  Just install it with synaptic, or in a terminal do
```
sudo apt-get install backuppc
```

---

### Post by varunanohar on 2007-09-07
hi 

ok fine. i got it but now i'm facing a problem 

Error: Unable to connect to BackupPC server
 when i enter [http://192.168.7.142/backuppc](http://192.168.7.142/backuppc)

now 4 this what to do.

Varuna Nohar

---

### Post by mocoloco on 2007-09-07
I'm not really familiar with BackupPC, I just saw it was in th repos.  You could check their [FAQ page]("http://backuppc.sourceforge.net/faq/index.html").
Or the manual page if one was included, by typing 
```
man backuppc
```.
Also you could search these forums.

Anyone else familiar with his issue?

---

