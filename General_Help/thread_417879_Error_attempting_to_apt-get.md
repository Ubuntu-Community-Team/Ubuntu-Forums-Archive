---
title: "Error attempting to apt-get"
date: 2007-04-22
forum: General Help
---

### Post by dta116 on 2007-04-22
I am trying to use apt-get update and I get an error:

~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

What am I doing wrong this time.....

---

### Post by taurus on 2007-04-22
```
**sudo** apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by desheikh on 2007-04-22
You need run apt-get as super user

# sudo apt-get update

rem you can only run one instance at a time so if you have synaptic or another apt command running at the same time the command wont wont work

---

