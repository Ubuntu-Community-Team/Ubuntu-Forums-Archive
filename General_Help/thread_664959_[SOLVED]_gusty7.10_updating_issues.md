---
title: "[SOLVED] gusty7.10 updating issues"
date: 2008-01-11
forum: General Help
---

### Post by Mrtim!3x on 2008-01-11
hi, i have just started updating my laptop with the updates there are 180 of them and i downloaded all of them but when the process gets to installing them i get an error message here it is as follows

E: dpkg was interrupted, you must manually run 'dpkg--configure -a' 
to correct the problem
E:_cache->open()failed, please report.

i know it happened because when i was in the middle of installing the updates the first time the battery was critically low and ubuntu automatically shut down the computer

now i get the error message when i want to update it

when i go to the terminal the run it after i hit enter it thinks and then it says that i do not have superuser privilege's to do that

i'm the only person who can logon and i have administrator access i know that.

anybody know what to do, besides reinstall ubuntu (which would be ok, i dont really have anything on it, i just dont want to go through the process again) 

and i'm kinda new at this, so i dont know much.

---

### Post by IOA on 2008-01-11
You don't have superuser privileges? Even if you have one account, Ubuntu hides a secret administrator account. It's not safe to be running it all the time, so Ubuntu hides it from you.

Type "su" into the terminal and enter your password. THEN you should be able to run that other command with superuser rights.

---

### Post by taurus on 2008-01-11
Open a terminal and run

```
sudo dpkg--configure -a
sudo apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

