---
title: "/var/cahce/apt/archives/lock"
date: 2008-02-27
forum: General Help
---

### Post by warrior24 on 2008-02-27
I get this error while trying to install software on my live usb in recursive mode. Tried 
sudo rm -rf /var/cache/apt/archives/lock      input/output error. 

sudo apt-get clean       segmentation fault 


E: Could not open lock file /var/cache/apt/archives/lock - open (5 Input/output error)

---

### Post by kesman on 2008-02-27
Maybe some other program is locking apt for being used? Check out some commands to see if this is happening:
```

ps -A | grep apt
ps -A | grep update

```
if something really is there locking up, kill the process.

---

### Post by warrior24 on 2008-03-02
heres what I get

---

### Post by warrior24 on 2008-03-02
bump

---

