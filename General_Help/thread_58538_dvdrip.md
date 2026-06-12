---
title: "dvd::rip"
date: 2005-08-20
forum: General Help
---

### Post by amcavoy on 2005-08-20
Alright, I have installed dvd::rip and configured it (for the most part), but I am still stuck on one thing.  What do I enter under "cdrecord device?"  Currently it has 0,X,0 but isn't working.  Does anyone know who has used this?

Thanks for your help.

---

### Post by poofyhairguy on 2005-08-21
[QUOTE=apmcavoy]Alright, I have installed dvd::rip and configured it (for the most part), but I am still stuck on one thing.  What do I enter under "cdrecord device?"  Currently it has 0,X,0 but isn't working.  Does anyone know who has used this?

Thanks for your help.[/QUOTE]

No one knew the answer here (I don't either) so I'm going to move this to see if someone who patrols another forum will help.

<doing my best>

---

### Post by amcavoy on 2005-08-21
Thank you very much.

---

### Post by arnieboy on 2005-08-21
[QUOTE=apmcavoy]Alright, I have installed dvd::rip and configured it (for the most part), but I am still stuck on one thing.  What do I enter under "cdrecord device?"  Currently it has 0,X,0 but isn't working.  Does anyone know who has used this?

Thanks for your help.[/QUOTE]0,X,0 stand for the values of bus, target and lun of your SCSI or ATAPI hard disk. The easiest way to get these values is to do a :
```
sudo cdrecord -scanbus
```
If this command shows errors owing to conflicts with kernel being >2.4 try putting the values as **1,2,0** instead of 0,X,0 and try checking the settings to see if its oks.
Let me know if this works.

---

### Post by amcavoy on 2005-08-21
The command didn't give me the info, but setting n,n,n=1,2,0 worked.  Thanks a lot for your help.

---

### Post by arnieboy on 2005-08-21
glad that I cud help :)

---

