---
title: "disable error messages - in 16.04.7"
date: 2020-11-17
forum: General Help
---

### Post by helen314 on 2020-11-17
During every boot I get not one, but series of error messages asking me to report them.
Then I get "...it has already been reported...".
I cannot identify the subject of error , the performance of Ubuntu seems to be OK . 
I like to disable these - superficial errors , for now.  

I do not wish to waste anybody's, including mine time , elaborating / justifying the errors,

**I like to disable them if possible. Period.**

---

### Post by deadflowr on 2020-11-17
This to remove the old crash reports.
```
cd /var/crash
sudo rm *
```

To disable apport
edit the file /etc/default/apport
change
enabled=1 to enabled=0
and save it.

---

