---
title: "[SOLVED] Problem installing Updates"
date: 2007-10-29
forum: General Help
---

### Post by Sulla158 on 2007-10-29
When I try to install updates to my already installed programs I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't know much about the terminal so i copied and pasted that into the terminal it said I needed superuser privileges.  I typed su but it asked for a password and I don't remember ever setting one.  I tried my normal password and leaving it blank, but neither one worked.  Any ideas?

---

### Post by taurus on 2007-10-29
Try

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Maestro23 on 2007-10-29
> **Sulla158 said:**
> When I try to install updates to my already installed programs I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't know much about the terminal so i copied and pasted that into the terminal it said I needed superuser privileges.  I typed su but it asked for a password and I don't remember ever setting one.  I tried my normal password and leaving it blank, but neither one worked.  Any ideas?

Need sudo:

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade

The password is your user password that you created when you installed Ubuntu.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Sulla158 on 2007-10-29
That fixed it. Thanks for the help.  I guess I should go back to work on learning how to use the command line.

---

