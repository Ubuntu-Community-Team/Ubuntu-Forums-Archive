---
title: "Software index is broken"
date: 2007-03-11
forum: General Help
---

### Post by STREETURCHINE on 2007-03-11
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2751 package `gdesklets':
 Configured-Version for package with inappropriate Status
rex@rex-desktop:~$

so i am getting these errors i have run the command 

```
sudo apt-get install -f
```

but it dosnt fix the problem as to line 2751 i tried to count but got lost ,there must be an easier way to get to line 2751

any ideas

---

### Post by taurus on 2007-03-11
```
sudo nano +2751 /var/lib/dpkg/status
```

---

### Post by STREETURCHINE on 2007-03-11
> **taurus said:**
> ```
sudo nano +2751 /var/lib/dpkg/status
```

thanks taurus i knew there had to be an easier way,
any way i think i fixed it

---

