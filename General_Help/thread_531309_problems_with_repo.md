---
title: "problems with repo"
date: 2007-08-21
forum: General Help
---

### Post by xGutsAndGloryx on 2007-08-21
i am having problems with the software sources program in ubuntu. its giving me the following error msg: E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable) E: Unable to lock the list directory.  I tried to add additional repo & change what server the ubuntu software is downloaded from. what should i do?

---

### Post by ddrichardson on 2007-08-22
The lock is because another program is running - ususally another synaptic or apt-get. Or it wasn't released by the last app to lock it.

If nothing is using it then you can delete the lock:```
sudo rm /var/lock/apt/lists/lock
```

Ensure nothing is locking it first though.

---

